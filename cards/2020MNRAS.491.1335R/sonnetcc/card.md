# Spiral arms in the protoplanetary disc HD100453 detected with ALMA: evidence for binary-disc interaction and a vertical temperature gradient

`2020MNRAS.491.1335R` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Rosotti, G. P. | arXiv: 1911.00518 | DOI: 10.1093/mnras/stz3090

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Do the scattered-light spiral arms of HD100453 have sub-mm continuum and CO counterparts launched by the stellar companion, and does the difference in spiral pitch angle between tracers reflect a vertical temperature gradient?  
  > "We thus confirm that the spirals are actual structures in the disc surface density and not only in the surface layers of the disc" (Introduction); "We then use these observations to test the hypothesis of (cite: juhasz_2018) that the spiral pitch angle should depend on the tracer." (Introduction)
- Target **HD100453**: coordinates _not stated_; z/distance 103 pc  
  > "HD100453A has a spectral type A9V (cite: Dominik2003) and a mass of 1.5 $M_\odot \pm 0.15$ (cite: Fairlamb)" (Introduction); "we assume a distance of 103pc (cite: 2016A&A...595A...1G; 2018A&A...616A...1G)" (4.1 Disc inclination and position angle); distance from Gaia (cite: 2016A&A...595A...1G; 2018A&A...616A...1G)  
  > "HD100453A has a spectral type A9V (cite: Dominik2003) and a mass of 1.5 $M_\odot \pm 0.15$ (cite: Fairlamb)" (Introduction); "we assume a distance of 103pc (cite: 2016A&A...595A...1G; 2018A&A...616A...1G)" (4.1 Disc inclination and position angle)

## Data provenance

- ALMA projects: 2017.1.01424.S
- bands: Band 7; four spectral windows centred on 345.79599, 343.810092, 331.80974 and 333.809798 GHz  
  > "The correlator was set up to use four spectral windows in Band 7, centred on 345.79599 GHz, 343.810092 GHz, 331.80974 GHz and 333.809798 GHz, respectively." (Observations)
- frequencies and spectral setup: SPW 1 FDM, 488.281 kHz channels (0.84 km/s after Hanning smoothing) for CO J=3-2; other three SPWs TDM for continuum  
  > "The first spectral window, centred on 345.79599 GHz, was set to Frequency Division Mode (FDM) with a channel spacing of 488.281 kHz, corresponding to 0.84 km/s velocity resolution after Hanning smoothing, to observe the CO J=3-2 line." (Observations); "The remaining three spectral windows were set to Time Division Mode (TDM) to observe the continuum." (Observations)
- continuum bandwidth: 1.875 GHz per spectral window (all four)  
  > "All four spectral windows had a bandwidth of 1.875 GHz." (Observations)
- arrays: 40 antennas  
  > "Our target was observed with 40 antennas with baselines ranging from 92 m to 8547 m" (Observations)
- configurations: _not stated_
- baselines: 92 m to 8547 m  
  > "Our target was observed with 40 antennas with baselines ranging from 92 m to 8547 m" (Observations)
- angular resolution: continuum 0.036 x 0.031 arcsec (robust 0.5); CO 0.054 x 0.052 arcsec (robust 2)  
  > "achieving a resolution of 0.036$''$ x 0.031$''$ and a beam position angle of -38.36$^\circ$" (Observations); "in this case the spatial resolution was 0.054$''$ x 0.052$''$ with a beam position angle of 83$^\circ$." (Observations)
- max recoverable scale: 0.6 arcsec  
  > "Formally, the maximum recoverable scale with this antenna configuration is 0.6$''$." (Observations)
- sensitivity: continuum rms 22 uJy/beam; CO rms 0.95 mJy/beam per channel  
  > "The rms noise level in the continuum was 22 $\mu$Jy/beam." (Observations); "The rms noise level was 0.95 mJy/beam in a single channel." (Observations)
- time on source: 1h 46min  
  > "the total on-source integration time was 1h 46min" (Observations)
- observing dates: 24 and 25 November 2017  
  > "on the 24th and 25th November 2017" (Observations)
- pi or archival as stated: PI: A. Juhász (not stated whether archival)  
  > "(Project ID 2017.1.01424.S, PI: A. Juhász)" (Observations)
- Line: CO J=3-2 (not stated)
- Other facility **SPHERE/VLT (scattered light)**: Near-infrared scattered-light image showing two symmetric spiral arms, compared with ALMA continuum  
  > "Scattered light imaging has shown that the system presents 2 symmetric spiral arms (cite: wagner_2015; benisty_2017)." (Introduction)
- External data: SPHERE R' scattered-light image of HD100453  
  > "(cite: benisty_2017), probing the disc atmosphere" (3.3 Comparison with scattered light observations) [from (cite: benisty_2017)]
- External data: Stellar mass 1.5 +/- 0.15 Msun used as Gaussian prior  
  > "a mass of 1.5 $M_\odot \pm 0.15$ (cite: Fairlamb)" (Introduction) [from (cite: Fairlamb)]
- External data: Distance 103 pc  
  > "we assume a distance of 103pc (cite: 2016A&A...595A...1G; 2018A&A...616A...1G)" (4.1 Disc inclination and position angle) [from (cite: 2016A&A...595A...1G; 2018A&A...616A...1G)]
- External data: Companion position (separation 1.05 arcsec, PA 132 deg)  
  > "The position of the companion (separation of 1.05$''$, at PA = 132$^\circ$) was taken from (cite: wagner_2015)." (4.2 Geometric toy model for the spiral arms) [from (cite: wagner_2015)]
- External data: Optical constants of astronomical silicates for Mie opacities  
  > "using the optical constants of astronomical silicates (cite: Weingartner2001)" (5.1.2 Radiative transfer) [from (cite: Weingartner2001)]
- Simulation/model as data: Three 3D FARGO3D hydrodynamical simulations (cold, hot, stratified) post-processed with RADMC-3D into 1.65 um and 880 um mock images  
  > "we perform a suite of 3D hydrodynamical simulations and then post-process them with a radiative transfer code to generate mock observations" (5.1 Methods); "We run three simulations." (5.1.1 Hydrodynamics)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "To calibrate the visibilities we used the ALMA pipeline and the Common Astronomy Software Applications (CASA, version 5.1.1; (cite: 2007ASPC..376..127M))." (Observations)
- casa version: CASA 5.1.1  
  > "the Common Astronomy Software Applications (CASA, version 5.1.1; (cite: 2007ASPC..376..127M))" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Tried for continuum and gas; no significant improvement, so not applied  
  > "Since self-calibration of both continuum and gas data did not significantly improve the images, we will base our analysis on the non-self-calibrated data." (Observations)

### Imaging

- task: CASA clean  
  > "The calibrated visibilities were imaged using the `clean` task in CASA." (Observations)
- deconvolver: _not stated_
- weighting robust: continuum: Briggs robust = 0.5; CO: robust = 2 (natural weighting)  
  > "we used Briggs weighting with a robust parameter value of 0.5" (Observations); "we used a robust parameter of 2 (corresponding to natural weighting)" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO channel maps smoothed with imsmooth to test for extended CO disc  
  > "we have lowered the resolution of our CO map, using the task `imsmooth` in CASA on the individual channel maps." (6.1 On the extent of the CO disc)
- final beam: continuum 0.036 x 0.031 arcsec, PA -38.36 deg; CO 0.054 x 0.052 arcsec, PA 83 deg  
  > "achieving a resolution of 0.036$''$ x 0.031$''$ and a beam position angle of -38.36$^\circ$" (Observations); "in this case the spatial resolution was 0.054$''$ x 0.052$''$ with a beam position angle of 83$^\circ$." (Observations)
- final rms: continuum 22 uJy/beam; CO 0.95 mJy/beam in a single channel  
  > "The rms noise level in the continuum was 22 $\mu$Jy/beam." (Observations); "The rms noise level was 0.95 mJy/beam in a single channel." (Observations)

### Inherited from earlier work

- Velocity-map fitting method for inclination and position angle (using eddy)  
  > "we fitted the projected velocity map following the method in (cite: 2018ApJ...868..113T) using the code `eddy`" (4.1 Disc inclination and position angle) [from (cite: 2018ApJ...868..113T)]
- Deprojection of scattered-light image onto a conical surface  
  > "we also take into account the fact that the emission comes from a conical surface, in the same way as done by (cite: benisty_2017)" (4.3 De-projected images) [from (cite: benisty_2017); method in (cite: 2016A&A...596A..70S)]
- Spiral wake equation used in the toy model  
  > "is given by the analytic wake equation for spiral waves in the linear regime by (cite: rafikov_2002a)" (4.2 Geometric toy model for the spiral arms) [from (cite: rafikov_2002a)]
- Vertical temperature prescription for the stratified simulation  
  > "we use the prescription commonly employed when fitting observations of (cite: dartois_2003) and subsequently updated by (cite: rosenfeld_2013)" (5.1.1 Hydrodynamics) [from (cite: dartois_2003); (cite: rosenfeld_2013)]
- Temperature ratio and disc aspect ratios chosen from a tailored radiative transfer model  
  > "This value, as well as the disc aspect ratios, were chosen based on the radiative transfer model, tailored for this system, presented in (cite: benisty_2017)" (5.1.1 Hydrodynamics) [from (cite: benisty_2017)]
- Dust grain size distribution dN/da ~ a^-3.5  
  > "(cite: 1977ApJ...217..425M)" (5.1.2 Radiative transfer) [from (cite: 1977ApJ...217..425M)]

### Not stated but needed to reproduce (our reading)

- CLEAN masks, thresholds, niter, deconvolver, cell and image size for continuum and CO imaging
- Which channels were used for continuum and whether any line-free channel selection or continuum subtraction was done
- Velocity range and rest frequency used for the CO moment maps, and clipping/threshold settings in bettermoments
- Details of the eddy fit (emission surface, free parameters, sampler settings, mask)
- Exact tracing procedure for spiral locations (radial ranges, number of points, which azimuth ranges) and the exact pipeline version
- Boundary conditions, resolution-dependent smoothing length and companion softening in FARGO3D; grain-size dependent mass fractions and star-companion setup files for RADMC-3D
- Flux calibrator and flux-scale uncertainty

## Analysis recipe

1. **Image continuum and CO**: CASA clean of pipeline-calibrated visibilities; continuum with Briggs robust 0.5, CO with natural weighting  
  > "The calibrated visibilities were imaged using the `clean` task in CASA." (Observations)
   - software: CASA
   - parameter: robust = 0.5 (continuum); robust = 2 (CO)  
  > "we used a robust parameter of 2 (corresponding to natural weighting)" (Observations)
   - fitting: _not stated_
   - validation: Self-calibration tried but did not significantly improve the images  
  > "Since self-calibration of both continuum and gas data did not significantly improve the images" (Observations)
2. **Measure continuum flux and high-pass filter to reveal spirals**: Total flux in a circular aperture around the ring; inverse Gaussian Fourier-space high-pass filter to reveal arms S1 and S2  
  > "We measure a total continuum flux in a circular aperture encompassing the extent of the ring of 510 mJy." (3.1 Continuum); "We chose an inverse Gaussian filter kernel, which we defined in the Fourier space as" (3.1 Continuum)
   - parameter: filter width sigma = 0.2 arcsec^-1  
  > "where $\nu$ is the spatial frequency and $\sigma$ is the width of the filter which we took to be 0.2 arcsec$^{-1}$." (3.1 Continuum)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit CO velocity map for inclination and position angle**: Keplerian fit of the first-moment map with eddy, Gaussian prior on stellar mass  
  > "we fitted the projected velocity map following the method in (cite: 2018ApJ...868..113T) using the code `eddy`" (4.1 Disc inclination and position angle)
   - software: eddy, bettermoments
   - parameter: stellar mass prior 1.5 +/- 0.15 Msun  
  > "We impose a Gaussian prior on the stellar mass of 1.5 $M_\odot \pm 0.15$ (cite: Fairlamb)" (4.1 Disc inclination and position angle)
   - assumption: distance 103 pc  
  > "we assume a distance of 103pc (cite: 2016A&A...595A...1G; 2018A&A...616A...1G)" (4.1 Disc inclination and position angle)
   - fitting: Gaussian prior on stellar mass; sampler and likelihood not stated  
  > "We impose a Gaussian prior on the stellar mass of 1.5 $M_\odot \pm 0.15$ (cite: Fairlamb)" (4.1 Disc inclination and position angle)
   - validation: Compared with previous inclination estimates; residuals inspected  
  > "which are in good agreement with previous investigations" (4.1 Disc inclination and position angle)
4. **Geometric toy model of projection effects on pitch angle**: 3D spiral wake from the analytic linear wake equation, projected at the disc orientation, with surface at z_p = 0.22 r_p versus midplane; compared isothermal and 2.5x temperature-difference cases  
  > "we employ a simple geometric toy model, in which the 3D cartesian coordinates of the spiral wake are given by" (4.2 Geometric toy model for the spiral arms)
   - parameter: aspect ratio 0.215  
  > "we use a value of 0.215" (4.2 Geometric toy model for the spiral arms)
   - parameter: inclination 33 deg, PA 145 deg, flaring index 0.04  
  > "We assumed a disc inclination of 33$^\circ$ , a position angle of 145$^\circ$  and a flaring index of 0.04" (4.2 Geometric toy model for the spiral arms)
   - parameter: temperature difference factor of 2.5 between midplane and surface  
  > "we assumed a temperature difference of a factor of 2.5 between the disc midplane and the surface layer" (4.2 Geometric toy model for the spiral arms)
   - assumption: m=2 spiral made by shifting the wake solution by 180 deg in azimuth  
  > "We artificially produce a m=2 spiral by shifting the solution of the spiral wake equation by 180$^\circ$ in azimuth." (4.2 Geometric toy model for the spiral arms)
   - fitting: _not stated_
   - validation: _not stated_
5. **Deproject images and measure spiral pitch angles**: Deproject using fitted inclination/PA (conical surface for scattered light, razor-thin disc for continuum); trace the radial emission maximum at each azimuth and fit an Archimedean spiral R = a phi + b  
  > "we trace the position of the spiral by looking at each azimuthal angle for the radial location corresponding to the maximum in emission" (4.3 De-projected images); "while we assume a razor-thin disc for the sub-mm continuum" (4.3 De-projected images)
   - parameter: pitch angle evaluated at projected radius 0.26 arcsec for the continuum spirals  
  > "these values are evaluated at a projected radius of 0.26$''$, corresponding to the mid-point of the radial range covered by the spirals" (4.3 De-projected images)
   - assumption: Archimedean and logarithmic models not distinguished given limited radial range  
  > "Given the limited radial range of the continuum spirals, we do not attempt to distinguish between an Archimedean" (4.3 De-projected images)
   - fitting: Least-squares-type fit with radial uncertainty set to the projected beam size; tracing points spaced by the beam  
  > "we assign a standard deviation of the radial position corresponding to the projected beam size" (4.3 De-projected images)
   - validation: Compared with geometric toy model and with hydrodynamical models  
  > "We conclude that the difference in pitch angles between the SPHERE and the ALMA data cannot be explained as a projection effect" (4.2 Geometric toy model for the spiral arms)
6. **Run 3D hydrodynamical simulations of binary-disc interaction**: FARGO3D spherical grid, point-mass companion, locally isothermal; cold (h=0.1), hot (h=0.2) and vertically stratified temperature (upper layers 4x midplane, z_q = 3H) runs  
  > "The simulations shown in this paper have been run with the code FARGO3D" (5.1.1 Hydrodynamics); "with the normalization set such that the disc aspect ratio at the location of the companion is 0.1 for the cold simulation and 0.2 for the hot simulation." (5.1.1 Hydrodynamics)
   - software: FARGO3D
   - parameter: grid 250 x 80 x 512 cells  
  > "We employ a spherical grid with 250, 80 and 512 cells" (5.1.1 Hydrodynamics)
   - parameter: M2/M1 = 0.17  
  > "The companion is treated like a point mass at a radius $r=1$, with a companion to star ratio $M_2/M_1=0.17$." (5.1.1 Hydrodynamics)
   - parameter: alpha viscosity 1e-3; images after 90 orbits at 30 au  
  > "a physical viscosity using the (cite: shakurasunyaev) prescription with a value of $\alpha=10^{-3}$" (5.1.1 Hydrodynamics); "All the images shown are after 90 orbits at a radius of 30 au (roughly 13 orbits at the companion location)." (5.1.1 Hydrodynamics)
   - parameter: upper-layer temperature 4x midplane; z_q = 3H  
  > "we assume that the temperature in the upper layers is 4 times the value in the midplane" (5.1.1 Hydrodynamics); "We also assume that $z_q=3H$, where H is the disc scale-height." (5.1.1 Hydrodynamics)
   - assumption: Locally isothermal equation of state; mean molecular weight 2.35  
  > "We employ a locally isothermal equation of state, in which the sound speed $c_s$ is a function of position only" (5.1.1 Hydrodynamics); "assuming a mean molecular weight of 2.35 to convert from temperature to sound speed" (5.1.1 Hydrodynamics)
   - fitting: _not stated_
   - validation: Steady state reached after about 10 companion orbits per cited work  
  > "the spiral structure settles into a steady state after 10 companion orbits" (5.1.1 Hydrodynamics)
7. **Generate mock images with radiative transfer and compare with data**: RADMC-3D thermal Monte Carlo then images at 1.65 um and 880 um using hydro gas density; compared deprojected, high-pass filtered polar images with SPHERE and ALMA  
  > "we calculate images in scattered light and sub-mm using the 3D radiative transfer code RADMC-3D" (5.1.2 Radiative transfer); "We plot all the images in polar coordinates" (5.2 Results)
   - software: RADMC-3D
   - parameter: 10^7 photons for thermal Monte Carlo and imaging  
  > "We use $10^7$ photons both for the thermal Monte Carlo simulations and for the image calculations." (5.1.2 Radiative transfer)
   - parameter: 10 log-spaced grain size bins, 0.1 um to 1 mm  
  > "We use 10 logarithmically spaced grain size bins between 0.1 $\mu$m and 1 mm" (5.1.2 Radiative transfer)
   - assumption: gas-to-dust ratio 100  
  > "We assume a gas-to-dust ratio of 100 to set the dust density." (5.1.2 Radiative transfer)
   - assumption: Stellar radiation as blackbody; Mie opacities of astronomical silicates  
  > "The radiation field of the central star is modelled with blackbody emission" (5.1.2 Radiative transfer); "The mass absorption coefficients of the dust grains are calculated with Mie-theory" (5.1.2 Radiative transfer)
   - fitting: _not stated_
   - validation: Qualitative comparison of simulated and observed pitch angles for cold, hot and stratified models  
  > "The comparison clearly shows that the stratified model is the only one capable of reproducing the pitch angles of the scattered light and sub-mm observations *at the same time*." (5.2 Results)
8. **Test for extended CO disc by smoothing**: Smooth CO channel maps with imsmooth to Band 6 resolution and recompute moment 8 map  
  > "We then recomputed the moment maps from the low resolution channel maps." (6.1 On the extent of the CO disc)
   - software: CASA
   - fitting: _not stated_
   - validation: Smoothed map closely resembles the earlier Band 6 map, so missing flux is unlikely to alter morphology  
  > "it does prove that, if we are missing some flux, the effect is too small to affect the morphology of the emission." (6.1 On the extent of the CO disc)

## Software

- **CASA** 5.1.1: Calibration, clean imaging, imsmooth  
  > "the Common Astronomy Software Applications (CASA, version 5.1.1; (cite: 2007ASPC..376..127M))" (Observations)
- **ALMA pipeline** : Calibrating the visibilities  
  > "To calibrate the visibilities we used the ALMA pipeline" (Observations)
- **eddy** : Fitting the projected velocity map for inclination and position angle  
  > "using the code `eddy`" (4.1 Disc inclination and position angle)
- **bettermoments** : Computing the first-moment (velocity) map  
  > "Computed using `bettermoments` (cite: bettermoments)" (Footnotes)
- **FARGO3D** : 3D hydrodynamical simulations of binary-disc interaction  
  > "The simulations shown in this paper have been run with the code FARGO3D" (5.1.1 Hydrodynamics)
- **RADMC-3D** : Radiative transfer mock images in scattered light and sub-mm  
  > "we calculate images in scattered light and sub-mm using the 3D radiative transfer code RADMC-3D" (5.1.2 Radiative transfer)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux in aperture around ring | 510 | not stated | mJy | 2 | We measure a total continuum flux in a circular aperture encompassing the extent of the ring of 510 mJy. |
| Central unresolved continuum flux | ~1.6 | not stated | mJy | 2 | and has a flux of $\sim 1.6$ mJy |
| Maximum continuum brightness temperature | 18 | not stated | K | 0 | the maximum brightness temperature across the image is 18 K |
| Disc inclination (eddy fit, stellar mass prior) | 35 | not stated | deg | 3 | The best-fit value is $35 \ensuremath{^\circ}$ for the disc inclination and $145 \ensuremath{^\circ}$ for the position angle |
| Disc position angle (eddy fit) | 145 | not stated | deg | 3 | The best-fit value is $35 \ensuremath{^\circ}$ for the disc inclination and $145 \ensuremath{^\circ}$ for the position angle |
| Fitted stellar mass | 1.27 | not stated | Msun | 3 | the fit converges to a stellar mass of 1.27 $M_\odot$ |
| Scattered-light pitch angle, eastern spiral | 14 | 2 | deg | 5 | For scattered light, we obtain an angle of 14$\pm$2$^\circ$ for the eastern spiral and 18$\pm$3$^\circ$ for the western spiral. |
| Scattered-light pitch angle, western spiral | 18 | 3 | deg | 5 | For scattered light, we obtain an angle of 14$\pm$2$^\circ$ for the eastern spiral and 18$\pm$3$^\circ$ for the western spiral. |
| Continuum pitch angle, eastern spiral S1 | 4.8 | 0.8 | deg | 5 | we obtain instead a value of 4.8$\pm$0.8$^\circ$ for the eastern spiral S1 and 6.6$\pm$1.5$^\circ$ for the western spiral S2 |
| Continuum pitch angle, western spiral S2 | 6.6 | 1.5 | deg | 5 | we obtain instead a value of 4.8$\pm$0.8$^\circ$ for the eastern spiral S1 and 6.6$\pm$1.5$^\circ$ for the western spiral S2 |
| 12CO pitch angle, eastern spiral | 19 | 3 | deg | 5 | The measured pitch angles in this case are 19$\pm$3$^\circ$ for the eastern spiral and 11$\pm$2$^\circ$ for the western one. |
| 12CO pitch angle, western spiral | 11 | 2 | deg | 5 | The measured pitch angles in this case are 19$\pm$3$^\circ$ for the eastern spiral and 11$\pm$2$^\circ$ for the western one. |
| 12CO southern spiral pitch angle at r>0.6 arcsec | 25 | 4 | deg | 5 | obtaining a pitch angle of 25$\pm$4$^\circ$ |

## Qualitative findings

- Two spiral arms are detected in sub-mm continuum (S1, S2) and two in CO (S3, S4); the southern CO spiral points to the companion position  
  > "This is the first source where we find counterparts in the sub-mm continuum to both scattered light spirals." (abstract); "The southern spiral points to the position of the companion" (3.2 CO J=3-2)
- CO disc extends only to ~0.3 arcsec; the apparently larger CO disc in lower-resolution data is likely the spirals blended with the disc  
  > "the large extent of the CO disc is likely an artefact of the low resolution, which does not allow one to distinguish the spirals from the disc" (6.1 On the extent of the CO disc)
- No strong sub-mm counterparts of the scattered-light shadows  
  > "there are no strong, obvious sub-mm counterparts of the NIR shadows" (6.2 On the origin of the spirals and model limitations)

## Claim tuples

- H: Do the scattered-light spirals have sub-mm continuum and CO counterparts, and is the companion the launching source? | E: High-resolution Band 7 continuum and CO J=3-2 imaging, high-pass filtering and overlay with SPHERE | R: Two continuum spirals and two CO spirals found; the southern CO spiral points to the companion | F: The spirals are real density structures launched by the companion | **supported**
- H: Does the spiral pitch angle differ between sub-mm continuum (midplane) and scattered light (upper layers)? | E: Deprojection and Archimedean spiral fits to the SPHERE and ALMA images | R: Continuum pitch angles 4.8 and 6.6 deg versus scattered light 14 and 18 deg | F: Scattered-light spirals are more open, and projection effects cannot explain it | **supported**
- H: Can binary-disc hydrodynamical simulations reproduce both pitch angles? | E: Cold, hot and vertically stratified FARGO3D runs post-processed with RADMC-3D | R: Only the stratified model matches both the scattered-light and sub-mm pitch angles | F: A colder midplane than upper layers is needed, supporting the vertical temperature gradient prediction | **supported**
- H: Is the CO disc truncated at about one third of the companion separation? | E: Compare the high-resolution CO map with CO smoothed to Band 6 resolution | R: CO disc extends only to ~0.3 arcsec; smoothed map resembles the Band 6 map | F: The orbit is compatible with being coplanar with the disc, though misalignment is not excluded | **partially**

## Reasoning

- Why this data: High resolution needed to resolve the spirals; some resolution sacrificed for CO surface brightness sensitivity  
  > "a clear detection of the southern spiral up to the companion position (see later) requires to sacrifice some spatial resolution in exchange for surface brightness sensitivity" (Observations)
- Why this method: Hydrodynamics plus radiative transfer used to test whether binary-disc interaction with a stratified temperature reproduces the observed pitch-angle difference  
  > "In order to test the hypothesis that the spirals arms seen in the ALMA and SPHERE observations are launched by the stellar companion" (5.1 Methods)
- Alternative: Shadow-launched spirals rejected: no strong sub-mm counterparts, CO spiral points to the companion, dust-dynamics simulations predict no sub-mm spiral  
  > "Given that all these facts rule out launching by shadows as origin for the spirals, it is possible that the special shadow location is just a lucky coincidence." (6.2 On the origin of the spirals and model limitations)
- Alternative: Projection effect as explanation of pitch angle difference rejected via toy model  
  > "We conclude that the difference in pitch angles between the SPHERE and the ALMA data cannot be explained as a projection effect" (4.2 Geometric toy model for the spiral arms)
- How they decided it was enough: _not stated_
- Limitation (authors): Maximum recoverable scale (0.6 arcsec) is smaller than the companion separation, so large-scale emission may be missed  
  > "in principle we might be missing information on the largest spatial scales" (Observations)
- Limitation (authors): Simulated spirals are asymmetric whereas observed scattered-light spirals are symmetric  
  > "the spirals in scattered light observations are symmetrical, while in the hydrodynamical simulations (see [7](#fig:model_comp)) we find that one spiral is stronger than the other." (6.2 On the origin of the spirals and model limitations)
- Limitation (authors): Assumed continuum spirals trace the same morphology as midplane gas spirals; untested  
  > "we have assumed that the spirals in the ALMA continuum image trace the same morphology as the spirals in the midplane gas" (6.2 On the origin of the spirals and model limitations)
- Caveat (inferred, ours): Pitch-angle fits use a hand-chosen tracing procedure with beam-based errors; sensitivity to tracing choices is not explored
- Caveat (inferred, ours): The comparison between models and data is qualitative (visual) with no quantitative fit to the simulations
- Caveat (inferred, ours): Gas density is used to set dust density for the sub-mm image, ignoring dust-gas decoupling for mm grains
- Caveat (inferred, ours): The inclination depends strongly on the stellar mass prior (30 vs 35 deg)

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Clean parameters (mask, threshold, niter, cell, image size) and channel selection
- Missing: Exact spiral tracing procedure and radial/azimuthal ranges
- Missing: Full hydro/radiative-transfer setup beyond the listed parameters (boundaries, grain-size mass weighting, plotting filters)
- Missing: Pipeline version and flux calibration details
- Data volume (inferred): Roughly 100-300 GB of raw visibilities for 2 execution blocks at 8.5 km baselines in Band 7 with one FDM window; calibrated measurement set tens of GB (inferred)
- Score (inferred): 3/5, Data project code and key imaging settings (robust, beam, rms) are given, but clean parameters, tracing procedure and simulation details are missing; hydro/RT parts need substantial inference.
- Rediscovery candidate: no, Public status of the data is not stated in the paper and the imaging and spiral-tracing recipe lacks key parameters; the hydrodynamical comparison is not numerically specified enough for a clean redo.

## Links

- Method: (cite: 2018ApJ...868..113T) (Velocity-map fitting method used with eddy)
- Method: (cite: 2016A&A...596A..70S) (Deprojection method for scattered-light images)
- Method: (cite: rafikov_2002a) (Analytic spiral wake equation)
- Companion: (cite: benisty_2017) (SPHERE scattered-light image and radiative transfer model of HD100453)
- Companion: (cite: vanderplas2019) (Earlier ALMA Band 6 observations of the same source)
- Companion: (cite: juhasz_2018) (Prediction that pitch angle depends on tracer)

## Checks

```json
{
 "quotes": 125,
 "quotes_ok": 125,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 113,
  "stated": 86,
  "rate": 0.761
 },
 "evidence_ok": true
}
```
