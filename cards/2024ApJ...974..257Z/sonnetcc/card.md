# Magnetic Fields in Massive Star-forming Regions (MagMaR). IV. Tracing the Magnetic Fields in the O-type Protostellar System IRAS 16547─4247

`2024ApJ...974..257Z` | The Astrophysical Journal 2024 | first author: Zapata, Luis A. | arXiv: 2408.10199 | DOI: 10.3847/1538-4357/ad701d

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Role and morphology of magnetic fields in the early evolution of the O-type protostellar system IRAS 16547-4247, traced by 1.2 mm dust polarization and molecular lines  
  > "The formation of the massive stars, and in particular, the role that the magnetic fields play in their early evolutionary phase is still far from being completely understood." (abstract)
- Target **IRAS16547-4247**: coordinates phase center RA 16h58m17.11s, Dec -42d52m07.06s (J2000.0)  
  > "This massive source is located at a distance of 2.9 $\pm$ 0.6 kpc (cite: rod2008)" (introduction); "The observations were pointed at the phase center" (Observations); z/distance 2.9 +/- 0.6 kpc  
  > "This massive source is located at a distance of 2.9 $\pm$ 0.6 kpc (cite: rod2008)" (introduction); "The observations were pointed at the phase center" (Observations); distance from Rodriguez et al. 2008 (cite: rod2008)  
  > "This massive source is located at a distance of 2.9 $\pm$ 0.6 kpc (cite: rod2008)" (introduction); "The observations were pointed at the phase center" (Observations)

## Data provenance

- ALMA projects: 2017.1.00101.S
- bands: 1.2 mm continuum (full polarization); lines near 244-261 GHz  
  > "Here, we present Atacama Large Millimeter/Submillimeter Array (ALMA) 1.2 mm full polarized continuum" (abstract)
- frequencies and spectral setup: Five SPWs; three centered at 243.518, 245.518, 257.521 GHz (1.875 GHz bandwidth, 1920 channels, 976.5 kHz = 1.195 km/s); two for H13CO+(3-2) and HN13C(3-2) with 243.7 kHz = 0.281 km/s channels  
  > "Three SPWs were centered at rest frequencies of 243.518, 245.518, and 257.521 GHz, and have a bandwidth of 1.875 GHz with a number of channels 1920" (Observations); "with a channel spacing of 0.281 km s$^{-1}$ or 243.7 kHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 45 antennas  
  > "At that time, the array included 45 antennas with diameters of only 12 m" (Observations)
- configurations: _not stated_
- baselines: 15 to 783 m (12 to 652 klambda)  
  > "covering baselines from 15 to 783 m" (Observations)
- angular resolution: continuum beam 0.44'' x 0.39'', PA -83.1 deg; line beam 0.36'' x 0.32'', PA -88.1 deg  
  > "with a synthesized beam of 0.44$''$ $\times$ 0.39$''$" (Observations); "with a synthesized beam of 0.36$''$ $\times$ 0.32$''$" (Observations)
- max recoverable scale: LAS 6.3''  
  > "The Largest Angular Scale (LAS) that is recovered by these observations is 6.3$''$." (Observations)
- sensitivity: Stokes I continuum RMS 0.2 mJy/beam (theoretical about 0.05); Stokes Q, U, V RMS 0.05 mJy/beam; line RMS 3 mJy/beam per channel  
  > "The resulting RMS-noise for the continuum image of the Stokes I is 0.2 mJy Beam$^{-1}$" (Observations); "for the Stokes Q, U, and V images the RMS noise level is 0.05 mJy Beam$^{-1}$" (Observations); "The resulting RMS-noise for the line images in Stokes I is 3 mJy Beam$^{-1}$ per channel spacing" (Observations)
- time on source: 45 min  
  > "The total on-source integration time was 45 min." (Observations)
- observing dates: 2018 December  
  > "were taken on 2018 December under the program 2017.1.00101.S" (Observations)
- pi or archival as stated: program 2017.1.00101.S, PI: Sanhueza, P.  
  > "under the program 2017.1.00101.S with PI: Sanhueza, P." (Observations)
- Line: H13CO+ 3-2 (260.25554 GHz)
- Line: HN13C 3-2 (261.26331 GHz)
- Line: CS 5-4 (244.93555 GHz)
- External data: Distance to IRAS16547-4247, 2.9 +/- 0.6 kpc  
  > "where D is the distance to IRAS16547$-$4247, 2.9 $\pm$ 0.6 kpc (cite: rod2008)" (Results and Discussion) [from (cite: rod2008)]
- External data: Dust mass opacity kappa = 0.0103 cm^2/g for gas-to-dust 100 at 1.2 mm  
  > "is the dust mass opacity for a gas-to-dust ratio of 100 appropriate for 1.2 mm (cite: hop1994)" (Results and Discussion) [from (cite: hop1994)]
- External data: Hot-gas association used to adopt Td = 150 K for IRAS 16547-E and -W  
  > "given that they are associated with hot molecular gas (cite: zap2019; tan2020)" (Results and Discussion) [from (cite: zap2019; tan2020)]
- External data: Systemic cloud velocity about -30 km/s  
  > "The systemic cloud velocity of IRAS16547$-$4247 is about $-$30 km s$^{-1}$ (cite: tan2020)." (Results and Discussion) [from (cite: tan2020)]
- External data: Free-free contribution to 1.2 mm emission of IRAS 16547-E is 3%  
  > "(3$\%$, arising from IRAS 16547-E) as discussed in (cite: zap2019)" (Results and Discussion) [from (cite: zap2019)]
- External data: DCF correction factor xi = 1/2 from simulations of turbulent clouds  
  > "is a correction factor derived from simulations of turbulent clouds (cite: 2001eve; liu2021)" (Magnetic Field Strength) [from (cite: 2001eve; liu2021)]

## Processing

### Calibration

- pipeline or manual: 'standard manner' with CASA; pipeline versus manual not specified  
  > "The ALMA data were calibrated, analyzed, and imaged in a standard manner" (Observations)
- casa version: CASA 5.4.0-68  
  > "Common Astronomy Software Applications (CASA) VERSION 5.4.0$-$68 (cite: casa2022)" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Quasars J1751+0939, J1517-2422, J1733-3722 used for bandpass, gain and flux amplitude calibration (roles not assigned per source)  
  > "Quasars J1751$+$0939, J1517$-$2422, and J1733$-$3722 were used to perform the bandpass calibration, the gain/atmospheric fluctuations, and the flux amplitude calibration." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-cal with Stokes I continuum as model, solution intervals inf., 60s, 15s; solutions applied to line channels  
  > "Phase self-calibration (using interval solutions that included: inf., 60s and 15s) was made using the continuum (Stokes I) as a model." (Observations); "The spectral line channels were then corrected with the acquired solutions." (Observations)

### Imaging

- task: CASA tclean  
  > "The resulting images were Fourier transformed, deconvolved, and restored using the CASA TCLEAN task." (Observations)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: continuum built from line-free channels in the SPWs (channel ranges not given)  
  > "we only used free-line channels in the SPWs" (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 0.44'' x 0.39'', PA -83.1 deg; lines 0.36'' x 0.32'', PA -88.1 deg  
  > "with a synthesized beam of 0.44$''$ $\times$ 0.39$''$" (Observations); "with a synthesized beam of 0.36$''$ $\times$ 0.32$''$" (Observations)
- final rms: Stokes I continuum 0.2 mJy/beam; Q, U, V 0.05 mJy/beam; lines 3 mJy/beam per channel  
  > "The resulting RMS-noise for the continuum image of the Stokes I is 0.2 mJy Beam$^{-1}$" (Observations); "for the Stokes Q, U, and V images the RMS noise level is 0.05 mJy Beam$^{-1}$" (Observations); "The resulting RMS-noise for the line images in Stokes I is 3 mJy Beam$^{-1}$ per channel spacing" (Observations)

### Inherited from earlier work

- Dust mass from the optically thin, isothermal expression of Hildebrand (1983)  
  > "assuming that the emission is optically thin, and isothermal, and following the expression (cite: hilde1983)" (Results and Discussion) [from (cite: hilde1983)]
- Column density estimate follows an earlier work  
  > "Following (cite: vic2014), we estimate a column density of" (Results and Discussion) [from (cite: vic2014)]
- DCF magnetic field strength derivation follows a standard pathway used in earlier papers  
  > "the derivation of the magnetic field strength follows a standard pathway (cite: Bel2019; San2021)" (Magnetic Field Strength) [from (cite: Bel2019; San2021)]
- Continuum RMS higher than theoretical, explained as in earlier case  
  > "As in other cases (cite: zap2023), the RMS-noise is higher than the theoretical" (Observations) [from (cite: zap2023)]

### Not stated but needed to reproduce (our reading)

- tclean weighting scheme and robust value, cell size, image size, niter, threshold and masks for continuum and lines
- Which SPW channel ranges were treated as line-free, and whether continuum subtraction was done for line cubes
- Polarization calibration: which source was the polarization angle and leakage calibrator, and how D-terms and X-Y phase were solved
- Flux density scale and its uncertainty (which calibrator set the scale, and the adopted flux)
- Pipeline versus manual calibration and whether one or several execution blocks were combined
- Which of the solution intervals (inf, 60s, 15s) were applied in which order and the number of self-cal rounds
- Polarization detection threshold (sigma cut on P and I) for plotted vectors, and vector sampling
- How the Gaussian source parameters in Table 1 were fitted (task, region, fit box) and how the envelope ellipses were chosen
- Exact pixel regions and velocity range of the three filaments used for DCF, and how line widths (Gaussian fit or moment) were measured
- Which temperature and velocity channels set the maximum brightness used for the 13-16 K gas temperature

## Analysis recipe

1. **calibrate and self-calibrate the visibilities**: Standard CASA calibration, then phase self-calibration using Stokes I continuum as model; solutions applied to line channels  
  > "The ALMA data were calibrated, analyzed, and imaged in a standard manner" (Observations); "Phase self-calibration (using interval solutions that included: inf., 60s and 15s) was made using the continuum (Stokes I) as a model." (Observations)
   - software: CASA
   - parameter: self-cal solution intervals: inf., 60s, 15s  
  > "using interval solutions that included: inf., 60s and 15s" (Observations)
   - fitting: _not stated_
   - validation: RMS improvement of almost a factor of 10 in continuum and 3 in line emission  
  > "The improvement in the continuum RMS-noise was almost a factor of 10 for the continuum, and 3 for the line emission." (Observations)
2. **image Stokes I, Q, U, V continuum and line cubes and form polarization maps**: tclean imaging; debiased polarized intensity, debiased polarization fraction and EVPA built from Q and U  
  > "The resulting images were Fourier transformed, deconvolved, and restored using the CASA TCLEAN task." (Observations); "We construct the images of the debiased linear polarized intensity" (Observations)
   - software: CASA, tclean
   - parameter: Continuum used line-free channels only  
  > "we only used free-line channels in the SPWs" (Observations)
   - parameter: Continuum Stokes I RMS 0.2 mJy/beam; Q, U, V RMS 0.05 mJy/beam  
  > "The resulting RMS-noise for the continuum image of the Stokes I is 0.2 mJy Beam$^{-1}$" (Observations); "for the Stokes Q, U, and V images the RMS noise level is 0.05 mJy Beam$^{-1}$" (Observations)
   - fitting: _not stated_
   - validation: Line image RMS similar to ALMA theoretical RMS  
  > "We obtained values similar to the ALMA theoretical RMS-noise for the spectral line images." (Observations)
3. **derive magnetic field orientations from EVPAs**: Field orientation taken orthogonal to the EVPA  
  > "we are assuming that these structures are orthogonal to the linear polarization orientations of the Electric Vector Position Angles (EVPAs)" (Results and Discussion)
   - assumption: Grains aligned by radiative torques  
  > "a result from grains aligned by Radiative Torques to precess around the magnetic field direction (cite: hog2008)" (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_
4. **measure continuum sources and derive dust masses and envelope properties**: Optically thin isothermal dust mass in the Rayleigh-Jeans regime; two-ellipsoidal-Gaussian fit to the central bi-conical envelope  
  > "assuming that the emission is optically thin, and isothermal, and following the expression (cite: hilde1983)" (Results and Discussion); "Using two ellipsoidal Gaussian fitting to the central bi-conical envelope" (Results and Discussion)
   - parameter: kappa = 0.0103 cm^2 g^-1, gas-to-dust 100, 1.2 mm  
  > "is the dust mass opacity for a gas-to-dust ratio of 100 appropriate for 1.2 mm" (Results and Discussion)
   - parameter: D = 2.9 kpc; observing frequency 250 GHz, Rayleigh-Jeans  
  > "We considered the Rayleigh$-$Jeans regime, given the observing frequency, 250 GHz." (Results and Discussion)
   - assumption: Td = 150 K for IRAS 16547-E and -W  
  > "Here, we are assuming a dust temperature T$_d$ = 150 K for IRAS 16547-E and IRAS 16547-W" (Results and Discussion)
   - assumption: Td = 50 K for the other sources  
  > "but for the rest sources we assume a T$_d$ = 50 K" (Results and Discussion)
   - assumption: Td = 16 K for the envelope, from the HN13C line  
  > "assuming a dust temperature of 16 K, a temperature obtained from HN$^{13}$C spectral line" (Results and Discussion)
   - fitting: Ellipsoidal Gaussian fits (sampler/priors not applicable or not stated)  
  > "Using two ellipsoidal Gaussian fitting to the central bi-conical envelope" (Results and Discussion)
   - validation: Masses of E and W agree with an earlier paper; mass uncertainty could be a factor of 3 or 4  
  > "The mass values for IRAS 16547-E and IRAS 16547-W are in very good agreement with those values obtained by (cite: zap2015)." (Results and Discussion); "the uncertainty in the mass estimation could be very large, a factor of up to 3 or 4" (Results and Discussion)
5. **build moment maps of H13CO+, HN13C and CS and compare with field vectors**: Moment 0 and 1 for H13CO+ and HN13C; Moment 8 and 1 for CS, over fixed velocity windows  
  > "To compute these moment maps we integrate over radial velocities from $-$40.9 km s$^{-1}$ to $-$15.9 km s$^{-1}$." (Results and Discussion); "To compute these moment maps we integrate over radial velocities from $-$49.7 km s$^{-1}$ to $-$11.3 km s$^{-1}$." (Results and Discussion); "we present the Moment 8 and 1 maps (maximum value of the spectrum, and radial velocity fields, respectively) of the CS(5$-$4) molecular emission" (Results and Discussion)
   - software: CASA
   - parameter: CS(5-4) window -64.4 to +9.64 km/s  
  > "To compute these moment maps we integrate over radial velocities from $-$64.4 km s$^{-1}$ to $+$9.64 km s$^{-1}$." (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_
6. **estimate plane-of-sky magnetic field strength with the DCF method in three filament regions**: Davis-Chandrasekar-Fermi method with B_pos ~ xi sigma_los / delta_psi * sqrt(4 pi rho) on filament-like regions with uniform fields and velocity coherence  
  > "we use the Davis-Chandrasekar-Fermi method (cite: dav1951; cha1953) to estimate the magnetic field strength within some structures" (Magnetic Field Strength); "The filaments are identified as velocity coherent structures in at least two different molecular transtions" (Magnetic Field Strength)
   - parameter: xi = 1/2  
  > "is a correction factor derived from simulations of turbulent clouds (cite: 2001eve; liu2021)" (Magnetic Field Strength)
   - parameter: sigma_los from HN13C after deconvolving the 0.28 km/s channel width and subtracting thermal broadening in quadrature  
  > "We extract the mean velocity dispersion from the optically thin tracer HN$^{13}$C after deconvolving with the channel width (0.28 km s$^{-1}$)" (Magnetic Field Strength)
   - parameter: delta_psi from polarization-angle standard deviation after subtracting mean angle uncertainty in quadrature  
  > "we subtract in quadrature the mean angle uncertainty of the measurements" (Magnetic Field Strength)
   - parameter: density from dust continuum mass in an assumed cylindrical volume  
  > "Assuming a cylindrical volume for each selected region, we find that the density varies between" (Magnetic Field Strength)
   - assumption: Dust temperature equals gas temperature, measured at the position of maximum brightness of the filaments; emission optically thin for density and mass  
  > "We assume that the dust temperature coincides with the gas temperature, which we measure at the position with the maximum brightness of the filaments within the velocity cube." (Magnetic Field Strength); "whereas assume optically thin emission in the filaments to measure the density and mass" (Magnetic Field Strength)
   - assumption: Uniform field orientation within each region  
  > "under the uniform magnetic field assumption" (Magnetic Field Strength)
   - fitting: _not stated_
   - validation: More than 40 Nyquist-sampled measurements per region; strong caution on resulting values  
  > "Each filament-like region comprises more than 40 independent Nyquist-sampled measurements, enough to secure a margin of error" (Magnetic Field Strength); "have to be used with extreme caution." (Magnetic Field Strength)

## Software

- **CASA** 5.4.0-68: Calibration, analysis and imaging of the ALMA data  
  > "Common Astronomy Software Applications (CASA) VERSION 5.4.0$-$68 (cite: casa2022)" (Observations)
- **tclean** : Fourier transform, deconvolution and restoration of images  
  > "The resulting images were Fourier transformed, deconvolved, and restored using the CASA TCLEAN task." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I continuum RMS | 0.2 | not stated | mJy/beam | 2 | The resulting RMS-noise for the continuum image of the Stokes I is 0.2 mJy Beam$^{-1}$ |
| Stokes Q, U, V RMS | 0.05 | not stated | mJy/beam | 2 | for the Stokes Q, U, and V images the RMS noise level is 0.05 mJy Beam$^{-1}$ |
| Polarization fraction in the region | ~2.0 | not stated | % | 2 | The polarization fraction is $\sim$2.0% in this region. |
| Envelope flux density (two-Gaussian fit) | 2.2 | 0.2 | Jy | 4 | we obtain a flux density of 2.2$\pm$0.2 Jy and a peak flux of 201$\pm$18 mJy Beam$^{-1}$ |
| Envelope peak flux | 201 | 18 | mJy/beam | 4 | we obtain a flux density of 2.2$\pm$0.2 Jy and a peak flux of 201$\pm$18 mJy Beam$^{-1}$ |
| Envelope total mass (Td = 16 K) | 220 | not stated | Msun | 4 | which corresponds to a total mass of 220 M$_\odot$, assuming a dust temperature of 16 K |
| Envelope column density | 4.0e26 | not stated | cm^-2 (as printed) | 4 | we estimate a column density of 4.0$\times$10$^{26}$ cm$^{-2}$, and a volumetric density of 2.2$\times$10$^{8}$ cm$^{-3}$ |
| Envelope volumetric density | 2.2e8 | not stated | cm^-3 | 4 | we estimate a column density of 4.0$\times$10$^{26}$ cm$^{-2}$, and a volumetric density of 2.2$\times$10$^{8}$ cm$^{-3}$ |
| Dust mass of IRAS16547E (Td = 150 K) | 6.1 | factor of up to 3 or 4 | Msun | 4 | 6.1 (150 K); the uncertainty in the mass estimation could be very large, a factor of up to 3 or 4 |
| Velocity gradient across HN13C emission | about 20 | not stated | km/s | 5 | The large velocity gradient (about 20 km s$^{-1}$) could be associated with the outflow. |
| Filament gas temperature | 13-16 | not stated | K | 6 | The resulting temperature ranges 13-16 K. |
| Filament total gas and dust mass | 55-75 | at least 25% | Msun | 6 | the total dust and gas mass enclosed in the filament-like regions amounts 55-75; the mass estimate (which adds at least another 25% uncertainty) |
| Filament mass density | 0.9 to 2.4e-16 | not stated | g cm^-3 | 6 | we find that the density varies between $0.9$ and $2.4\times10^{-16}$ g cm$^{-3}$ |
| Thermal line broadening of HN13C at 16 K | 0.07 | not stated | km/s | 6 | takes the value of 0.07 km s$^{-1}$. |
| Plane-of-sky magnetic field strength in filaments | 2.0 to 6.1 | about 0.4-0.7 mG from spectral resolution, plus at least 25% mass | mG | 6 | The derived mean magnetic field strength in the regions goes from 2.0 to 6.1 mG; which dominates the error propagation in the B field strength measurements, $\approx0.4-0.7$ mG |
| Alfven speed in filaments | 0.5 to 1.1 | not stated | km/s | 6 | from 0.5 to 1.1 km s$^{-1}$ |
| Eturb/Emag | 0.1 to 0.4 | not stated | dimensionless | 6 | We obtain values between 0.1 and 0.4, suggesting that the magnetic energy would be larger than turbulence in these filaments |

## Qualitative findings

- A dusty bi-conical envelope of about 10,000 au surrounds IRAS16547-E and -W, likely carved by the thermal radio jet  
  > "This envelope has a bi-conical structure likely carved by the powerful thermal radio jet present in region." (abstract)
- Magnetic field vectors follow the envelope and some seem to converge on IRAS16547-E and -W  
  > "The magnetic fields vectors follow very-well the bi-conical envelope." (abstract); "Some of these vectors seem to converge to IRAS 16547-E, and IRAS 16547-W" (abstract)
- Velocity gradients in H13CO+ and HN13C correspond with the field and may trace outflow cavities or in places infall  
  > "show velocity gradients with a good correspondence with the magnetic fields" (abstract)
- CS(5-4) shows multiple outflow cavities or bow-shocks with different orientations, some following the NW-SE jet  
  > "We also find that the CS(5$-$4) molecular line emission reveals multiple outflow cavities or bow-shocks with different orientations" (abstract)

## Claim tuples

- H: Does the 1.2 mm dust continuum reveal an envelope shaped by the thermal jet around the massive protostars? | E: 1.2 mm Stokes I imaging and Gaussian fitting of the central envelope | R: Bi-conical envelope of about 10,000 au; envelope mass 220 Msun (Td = 16 K) | F: The envelope is likely carved by the NW-SE radio thermal jet | **partially**
- H: Do the magnetic field vectors trace the envelope and converge on the massive protostars? | E: EVPA maps rotated by 90 deg overlaid on the continuum | R: Vectors follow the bi-conical envelope; some converge to IRAS16547-E and -W; polarization fraction about 2.0% | F: Field follows outflow-carved envelope; infall interpretation is left speculative | **partially**
- H: Do gas velocity fields correspond with the magnetic field structure? | E: Moment 1 maps of H13CO+(3-2) and HN13C(3-2) overlaid with polarization vectors | R: Velocity gradients (about 20 km/s for HN13C SE to NW) correspond with the field | F: Gradients maybe trace outflow cavities, or in parts infall | **partially**
- H: How strong is the magnetic field in filamentary regions, and does it dominate over turbulence? | E: DCF method on three filament-like regions using HN13C dispersion and polarization angle dispersion | R: B_pos 2.0 to 6.1 mG; Alfven speed 0.5 to 1.1 km/s; Eturb/Emag 0.1 to 0.4 | F: Magnetic energy larger than turbulence in these filaments, but values to be used with extreme caution | **partially**
- H: What produces the multiple ejections seen in CS(5-4)? | E: CS(5-4) Moment 8, Moment 1 and channel maps | R: Several bow-shocks and outflow cavities with different orientations; jet would precess more than 150 deg on the plane of the sky | F: Strong precession of the central binary or additional CO outflows could explain them | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: DCF chosen because the polarization segments in the filaments have near-constant orientation  
  > "The morphology of the polarization segments eases the usage of the DCF method, since we can assume a field with constant orientation." (Magnetic Field Strength)
- Alternative: xi = 0.22 for strong fields in cylinders would give field strengths a factor of two lower; classical xi = 1/2 adopted  
  > "acknowledging that the field strengths could be a factor of two lower only due to geometry issues." (Magnetic Field Strength)
- Alternative: Infall dusty envelope interpretation of the field is considered but left speculative  
  > "however, here we only leave this as a speculative possibility." (Results and Discussion)
- How they decided it was enough: More than 40 independent Nyquist-sampled measurements per region taken as sufficient statistics  
  > "Each filament-like region comprises more than 40 independent Nyquist-sampled measurements, enough to secure a margin of error" (Magnetic Field Strength)
- Limitation (authors): Thermal dust and free-free emission cannot be separated for IRAS16547-E and -W at these wavelengths  
  > "cannot separate the thermal dust, and free-free emission at these millimeter wavelengths" (Results and Discussion)
- Limitation (authors): Dust mass uncertain by up to a factor of 3 or 4 (temperature and opacity)  
  > "the uncertainty in the mass estimation could be very large, a factor of up to 3 or 4" (Results and Discussion)
- Limitation (authors): Extended continuum emission may be missing  
  > "we may be missing some more extended continuum millimeter emission" (Results and Discussion)
- Limitation (authors): DCF results have large uncertainty from finite spectral resolution and mass estimate  
  > "have to be used with extreme caution." (Magnetic Field Strength)
- Caveat (inferred, ours): Continuum RMS is 4x above theoretical and dynamic range limited by the bright source, which affects faint source and polarization fraction detections
- Caveat (inferred, ours): DCF applied with a single assumed xi and no Monte Carlo uncertainty; B_pos errors only loosely quantified
- Caveat (inferred, ours): Summary says the 6.1 mG value is at the central source, while the filament table assigns 5.2-6.1 mG to the West region
- Caveat (inferred, ours): Temperatures of 13-16 K from a marginally optically thick line peak conflict with 50-150 K assumed for compact sources, and the 220 Msun envelope mass is sensitive to that choice
- Caveat (inferred, ours): Polarization calibration and polarization thresholds are not described

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Polarization calibrators and leakage calibration steps
- Missing: tclean parameters (weighting, robust, cell, image size, masks, thresholds)
- Missing: Line-free channel selection and continuum subtraction details
- Missing: Source-fitting procedure for Table 1 and region definitions for the DCF filaments
- Missing: Polarization significance cuts and vector sampling
- Data volume (inferred): About 10-30 GB for a single 12 m execution block (45 min on source, five SPWs, full polarization) in the archive; reproduction needs the raw MS plus calibration scripts
- Score (inferred): 2/5, Project code and main settings (SPWs, beam, RMS, self-cal intervals, CASA version) are given and numeric results are listed, but polarization calibration, tclean parameters and region definitions are missing and the paper does not state data availability.
- Rediscovery candidate: no, The recipe lacks polarization calibration and imaging parameters and the paper does not state that the data are public, so the main numbers cannot be redone from the text alone.

## Links

- Method: CASA Team et al. 2022 (cite: casa2022) (CASA software used for calibration and imaging)
- Method: Hildebrand 1983 (cite: hilde1983) (dust mass formula)
- Method: Davis 1951; Chandrasekhar & Fermi 1953 (cite: dav1951; cha1953) (DCF method for field strength)
- Method: Liu et al. 2021 (cite: liu2021) (DCF correction factor xi for cylinders)
- Companion: Zapata et al. 2019 (cite: zap2019) (earlier ALMA study of the circumbinary disk and hot core in IRAS16547-4247)
- Companion: Tanaka et al. 2020 (cite: tan2020) (disks and jet of IRAS16547-Ea, systemic velocity)
- Companion: Sanhueza et al. 2021 (cite: San2021) (similar DCF pathway applied to IRAS 18089-1732)
- Companion: Zapata et al. 2023 (cite: zap2023) (other case with RMS above theoretical)
- Related: MagMaR (Magnetic Fields in Massive Star-forming Regions), paper IV
- Related: ALMA program 2017.1.00101.S

## Checks

```json
{
 "quotes": 127,
 "quotes_ok": 127,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 73,
  "rate": 0.737
 },
 "evidence_ok": true
}
```
