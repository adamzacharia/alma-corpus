# Gravity and Rotation Drag the Magnetic Field in High-mass Star Formation

`2020ApJ...904..168B` | The Astrophysical Journal 2020 | first author: Beuther, Henrik | arXiv: 2010.05825 | DOI: 10.3847/1538-4357/abc019

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: Whether gravity, rotation and/or magnetic fields dominate the dynamics, and shape the magnetic field morphology, in the high-mass star-forming hot core G327.3  
  > "The main question we address is whether gravity, rotation and/or magnetic fields are dominating the dynamics in this region." (Introduction)
- Target **G327.3**: coordinates phase center R.A. (J2000.0)=15:53:07.72, Decl. (J2000.0)=-54:37:06.1  
  > "This region is at a distance of $\sim$3.1 kpc" (Introduction); "The phase center of G327.3 was R.A. (J2000.0)=15:53:07.72 and Decl. (J2000.0)=$-$54:37:06.1" (Observations); z/distance ~3.1 kpc (v_lsr = -46.0 km/s)  
  > "This region is at a distance of $\sim$3.1 kpc" (Introduction); "The phase center of G327.3 was R.A. (J2000.0)=15:53:07.72 and Decl. (J2000.0)=$-$54:37:06.1" (Observations); distance from (cite: caswell1995; wyrowski2006)  
  > "This region is at a distance of $\sim$3.1 kpc" (Introduction); "The phase center of G327.3 was R.A. (J2000.0)=15:53:07.72 and Decl. (J2000.0)=$-$54:37:06.1" (Observations)

## Data provenance

- ALMA projects: 2018.1.01449.S
- bands: 1.3 mm band  
  > "The source was observed in the 1.3 mm band with four spectral windows centered at 230.852, 229.152, 216.422 and 214.535 GHz." (Observations)
- frequencies and spectral setup: 4 spectral windows centered at 230.852, 229.152, 216.422 and 214.535 GHz; first window 0.9375 GHz wide at 0.977 MHz resolution, other three 1.874 GHz wide at 1.953 MHz resolution  
  > "The source was observed in the 1.3 mm band with four spectral windows centered at 230.852, 229.152, 216.422 and 214.535 GHz." (Observations); "While the first window had a width and spectral resolution of 0.9375 GHz and 0.977 MHz, respectively, the other three spectral windows had a width and resolution of 1.874 GHz and 1.953 MHz, respectively." (Observations)
- continuum bandwidth: whole bandpass collapsed for Stokes I, Q and U, excluding the CO(2–1) line  
  > "For all Stokes products (I, Q and U), we collapsed the whole bandpass but excluding the CO(2–1) spectral line." (Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 14 to 331 m, 41 to 43 effective antennas  
  > "In total, 41 to 43 effective antennas were in the array, covering baselines between 14 and 331 m." (Observations)
- angular resolution: 1.16'' x 0.96'' (PA 81.4 deg) at robust = 0.5  
  > "the final data products presented here were imaged with a robust parameter of 0.5, resulting in a spatial resolution of $1.16''\times 0.96''$ (PA. 81.4 deg)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: Stokes I rms 1.5 mJy/beam; linearly polarized P rms 5 uJy/beam; 13CH3CN channel rms ~7.3 mJy/beam (3 km/s channels)  
  > "images are 1.5 mJy beam$^{-1}$ and 5 $\mu$Jy beam$^{-1}$, respectively." (Observations); "The $1\sigma$ rms value within each channel is roughly 7.3 mJy beam$^{-1}$." (Observations)
- time on source: ~40 min per scheduling block, ~2 h in total  
  > "The on-source time for G327.3 was roughly 40 min per scheduling block, hence $\sim$2 h on-source time in total." (Observations)
- observing dates: March 25, 2019 (three observing blocks of roughly 101, 99 and 112 min)  
  > "The three observing blocks were observed on March 25, 2019, with total observing times of roughly 101, 99 and 112 min, respectively." (Observations)
- pi or archival as stated: _not stated_
- Line: 13CH3CN 12_4-11_4 (E_u/k_b = 181 K) (214.310 GHz)
- Line: CO 2-1 (used for outflow/inclination; excluded from continuum) (not stated)
- External data: Distance ~3.1 kpc, luminosity ~10^5 Lsun and mass reservoir ~950 Msun of G327.3  
  > "This region is at a distance of $\sim$3.1 kpc and has a luminosity of $\sim 10^5$ L$_{\odot}$ and a mass reservoir of $\sim$950 M$_{\odot}$ (cite: caswell1995; wyrowski2006)." (Introduction) [from (cite: caswell1995; wyrowski2006)]
- External data: Average dust temperature of 100 K for the typical hot core, used for the mass estimate  
  > "Assuming optically thin dust continuum emission at an average temperature of this typical hot core of 100 K (cite: beuther2009c)" (3 Quantitative analysis) [from (cite: beuther2009c)]
- External data: Gas-to-dust mass ratio of 150  
  > "a gas-to-dust mass ratio of 150 (cite: draine2011)" (3 Quantitative analysis) [from (cite: draine2011)]
- External data: Dust absorption coefficient kappa = 1.11 cm^2 g^-1 at densities of 10^8 cm^-3  
  > "using a dust absorption coefficient $\kappa = 1.11$ cm$^2$g$^{-1}$ at densities of $10^8$ cm$^{-3}$ (cite: ossenkopf1994)" (3 Quantitative analysis) [from (cite: ossenkopf1994)]
- External data: Critical mass-to-flux ratio used to set the simulation's initial field (20 times critical)  
  > "with a mass-to-flux ratio of 20 times the critical value (cite: crutcher2012)" (Simulations) [from (cite: crutcher2012)]
- Simulation/model as data: 2D axisymmetric radiation-MHD collapse simulation (Pluto 4.1) of a magnetized 100 Msun pre-stellar core, 0.1 pc radius, weak field (mass-to-flux 20x critical), compared at 30 kyr when a 17 Msun protostar has formed  
  > "The model describes the gravitational collapse of a magnetized pre-stellar core of 100 solar masses of gas and dust within a sphere of 0.1 pc in radius." (Simulations); "At the simulation time of 30 kyrs after the start of collapse a 17 M$_{\odot}$ protostar has formed at the center." (Simulations)

## Processing

### Calibration

- pipeline or manual: CASA pipeline, following the ALMA provided calibration scripts  
  > "Calibration was done with the CASA pipeline version 5.6.1 following the ALMA provided calibration scripts." (Observations)
- casa version: CASA pipeline version 5.6.1  
  > "Calibration was done with the CASA pipeline version 5.6.1 following the ALMA provided calibration scripts." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1427-4206 (also bandpass); phase J1603-4904; polarization J1550+0527  
  > "As phase calibrator we used the quasar J1603-4904, the polarization calibration was conducted with J1550+0527, and bandpass and flux calibrations were done with J1427-4206." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Applied within CASA; improved the Stokes I continuum rms by more than a factor 3  
  > "Self-calibration was applied within CASA improving especially the rms in the Stokes I continuum image by more than a factor 3." (Observations)

### Imaging

- task: tclean in CASA, experimenting with different robust parameters  
  > "We imaged the data with the tclean task in CASA experimenting with different robust parameters." (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5, chosen to optimize sensitivity of the polarized emission in Stokes Q and U  
  > "To optimize for the sensitivity of the polarized emission in Stokes Q and U, the final data products presented here were imaged with a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: essentially no line-free continuum in Stokes I; continuum made from whole bandpass excluding CO(2–1)  
  > "Since these are high-sensitivity data and the region is a line-rich hot core, there is essentially no line-free continuum part in the data." (Observations); "For all Stokes products (I, Q and U), we collapsed the whole bandpass but excluding the CO(2–1) spectral line." (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.16'' x 0.96'' (PA 81.4 deg)  
  > "resulting in a spatial resolution of $1.16''\times 0.96''$ (PA. 81.4 deg)" (Observations)
- final rms: Stokes I 1.5 mJy/beam; P 5 uJy/beam; 13CH3CN 7.3 mJy/beam per 3 km/s channel  
  > "images are 1.5 mJy beam$^{-1}$ and 5 $\mu$Jy beam$^{-1}$, respectively." (Observations); "The data were imaged with the (almost) native spectral resolution of 3 km s$^{-1}$." (Observations)

### Inherited from earlier work

- Calibration follows the ALMA-provided calibration scripts  
  > "following the ALMA provided calibration scripts" (Observations) [from ALMA provided calibration scripts]
- Polarization de-biasing and sigma_P estimate  
  > "where $\sigma_Q$ and $\sigma_U$ are the rms values of the Stokes Q and U images (cite: dallolio2019)." (Observations) [from (cite: dallolio2019)]
- Polarization angles usable beyond the inner 1/3 of the primary beam (out to at least 10'') by combining nearby pointings  
  > "recent analysis of nearby pointings in polarization data revealed that they can be combined also over more extended scales within the primary beam and for mosaics (cite: beuther2018; hull2020)." (Observations) [from (cite: beuther2018; hull2020)]
- Histogram of relative orientations method  
  > "This is done quantitatively by means of the histogram of relative orientations (HRO) introduced for the Planck magnetic field studies (cite: soler2013; soler2016; soler2019b)." (Histogram of Relative Orientations (HRO)) [from (cite: soler2013; soler2016; soler2019b)]
- Rayleigh test Z and projected Rayleigh test V statistics  
  > "the Rayleigh test $Z$ and the projected Rayleigh test $V$ (cite: brazier1994; jow2018)" (Histogram of Relative Orientations (HRO)) [from (cite: brazier1994; jow2018)]
- Simulation set-up merges and simplifies two earlier modeling scenarios  
  > "The comparison simulation was carried out by basically merging and simplifying two recent modeling scenarios (cite: koelligan2018; kuiper2018)." (Simulations) [from (cite: koelligan2018; kuiper2018)]
- Ohmic dissipation strength follows Machida et al., neglecting gas-temperature dependence  
  > "For the dissipation strength, we follow (cite: machida2007), but neglect the dependence on gas temperature." (Simulations) [from (cite: machida2007)]
- phi map presented in the style of the sin(omega) maps  
  > "similar to the sin$(\omega)$ maps presented in (cite: koch2018)" (Histogram of Relative Orientations (HRO)) [from (cite: koch2018)]

### Not stated but needed to reproduce (our reading)

- Self-calibration details: number of rounds, solint, and which data/solutions were applied
- tclean settings: image size, cell size, deconvolver, masking and thresholds, niter, primary-beam correction
- Polarization calibration details beyond naming J1550+0527 (leakage and angle calibration steps) and how Q/U were imaged and combined across the three EBs
- Spectral image set-up for 13CH3CN moment 1 (channel range, clipping threshold, moment method)
- HRO set-up: bin edges and number of radial bins, gradient/isophote computation, smoothing, sigma_P/P cut (only hinted at in figure file names), and the center position used for the radial bins
- Aperture definition for the 331 Msun mass within 2'' and the 3-sigma contour definitions for C, NE1, NE2
- How the simulated magnetic field was projected/rotated and compared with the observed map (no quantitative comparison described)
- Public availability of the data and the archive product versions are not stated

## Analysis recipe

1. **calibrate and image Stokes I, Q, U continuum**: CASA pipeline calibration, self-calibration, tclean imaging of Stokes I, Q and U with the full bandpass collapsed excluding CO(2–1)  
  > "Calibration was done with the CASA pipeline version 5.6.1 following the ALMA provided calibration scripts." (Observations); "We imaged the data with the tclean task in CASA experimenting with different robust parameters." (Observations)
   - software: CASA, tclean
   - parameter: robust = 0.5  
  > "the final data products presented here were imaged with a robust parameter of 0.5" (Observations)
   - parameter: self-calibration lowered Stokes I rms by more than a factor 3  
  > "Self-calibration was applied within CASA improving especially the rms in the Stokes I continuum image by more than a factor 3." (Observations)
   - assumption: Q and U continuum is not significantly line contaminated, so it represents the true polarized continuum  
  > "the linearly polarized Q and U datasets should represent the real polarized continuum well without significant line contamination." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **derive de-biased polarized intensity and magnetic-field vectors**: De-bias with sigma_P from Q and U rms, compute P, rotate polarization angles by 90 deg to get the magnetic field direction  
  > "We de-biased the polarization data by estimating the rms" (Observations); "we rotated all angles by 90 deg and show these rotated angles outlining the direction of the magnetic field" (Morphologies and kinematics)
   - parameter: P = sqrt(Q^2+U^2-sigma_P^2), rms of P 5 uJy/beam  
  > "linearly polarized $P=\sqrt{Q^2+U^2-\sigma_P^2}$ images" (Observations); "images are 1.5 mJy beam$^{-1}$ and 5 $\mu$Jy beam$^{-1}$, respectively." (Observations)
   - assumption: Polarized emission comes from dust grains whose rotation axis is aligned with the local magnetic field, so B is perpendicular to the polarization angle  
  > "Assuming that the polarized emission is produced by dust grains gyrating around a rotation axis that is aligned with the local magnetic fields" (Morphologies and kinematics)
   - assumption: Bulk of dust emission is optically thin, with little scattering contribution  
  > "the bulk of the emission is optically thin." (Observations)
   - fitting: _not stated_
   - validation: Polarization angles treated as trustworthy out to at least 10'' from the field center  
  > "the polarized emission and the associated polarization angles are trustworthy out to at least $10''$ from the field center." (Observations)
3. **map gas kinematics with 13CH3CN**: First-moment (intensity-weighted peak velocity) map of 13CH3CN(12_4-11_4) imaged at ~3 km/s resolution  
  > "The right panel of Fig. [1](#pol_all) shows the first moment map (intensity-weighted peak velocities) of the dense gas" (Morphologies and kinematics); "The data were imaged with the (almost) native spectral resolution of 3 km s$^{-1}$." (Observations)
   - parameter: channel rms ~7.3 mJy/beam  
  > "The $1\sigma$ rms value within each channel is roughly 7.3 mJy beam$^{-1}$." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **derive dust masses and column densities**: Peak and integrated flux densities within the 3-sigma contours of C, NE1 and NE2, converted to mass and column density assuming optically thin dust  
  > "we derived the peak flux densities and the integrated fluxes within the $3\sigma$ contours for the main central contiguous structure" (Masses, column densities and magnetic field strengths)
   - parameter: T = 100 K, gas-to-dust 150, kappa = 1.11 cm^2/g  
  > "a gas-to-dust mass ratio of 150 (cite: draine2011)" (Masses, column densities and magnetic field strengths); "using a dust absorption coefficient $\kappa = 1.11$ cm$^2$g$^{-1}$ at densities of $10^8$ cm$^{-3}$ (cite: ossenkopf1994)" (Masses, column densities and magnetic field strengths)
   - assumption: Optically thin dust emission at an average temperature of 100 K  
  > "Assuming optically thin dust continuum emission at an average temperature of this typical hot core of 100 K (cite: beuther2009c)" (Masses, column densities and magnetic field strengths)
   - assumption: Distance 3.1 kpc  
  > "At 3.1 kpc distance that corresponds to a radius of 6200 AU." (Masses, column densities and magnetic field strengths)
   - fitting: _not stated_
   - validation: Uncertainty propagated from a factor 2 in temperature (and factor 2 in kappa gives up to a factor 4); numbers called rough estimates  
  > "Adding a factor 2 uncertainty for the dust absorption coefficient, the mass uncertainty can be as high as a factor 4." (Masses, column densities and magnetic field strengths)
5. **test whether the inner structure can be centrifugally supported and constrain inclination**: Equate centrifugal and gravitational forces at r = 6200 AU with 331 Msun enclosed to get v = 6.9 km/s, compare to the observed ~1 km/s over the radius, correcting with sin(i)  
  > "Assuming equilibrium between the centrifugal and gravitational forces at the outer radius $r$ of the disk, the velocity $v$ corresponding to the enclosed dynamical mass $M$ can be estimated via" (Masses, column densities and magnetic field strengths); "To account for the projection in the observations, we need to multiply the above equation with $sin(i)$" (Masses, column densities and magnetic field strengths)
   - parameter: M = 331 Msun within 2'' (6200 AU) radius  
  > "we find approximately 331 M$_{\odot}$" (Masses, column densities and magnetic field strengths)
   - assumption: Mass from dust continuum only; magnetic breaking and inclination are degenerate  
  > "In principle, not just projection but also magnetic breaking can reduce the observed velocities, and these two parameters are degenerate." (Masses, column densities and magnetic field strengths)
   - fitting: _not stated_
   - validation: CO(2–1) high-velocity gas with red and blue peaks separated by ~1'' supports a near face-on geometry  
  > "This indicates that we are looking almost face-on into a rotating and collapsing system where the outflow is roughly along the line of sight." (Morphologies and kinematics)
6. **quantify field vs. density-structure orientation with HRO**: Histogram of relative orientations between the magnetic field and Stokes I isophote contours as a function of distance from the peak; mean angle, Rayleigh Z and projected Rayleigh V; phi map  
  > "This distribution is characterized by the mean orientation angle $\left<\phi\right>$ and two statistical tests from circular statistics, the Rayleigh test $Z$ and the projected Rayleigh test $V$ (cite: brazier1994; jow2018)." (Histogram of Relative Orientations (HRO))
   - parameter: random-distribution expectation for V is +/- sqrt(2)  
  > "significantly above from what is expected for a random distribution of angles, $\pm\sqrt{2}$" (Histogram of Relative Orientations (HRO))
   - fitting: _not stated_
   - validation: V significantly above random in the outer bins; central bins consistent with random  
  > "Getting close to the center, the orientation between magnetic field and contours becomes less perpendicular and again consistent with a random distribution." (Histogram of Relative Orientations (HRO))
7. **compare with a magnetized-collapse MHD simulation**: Qualitative and energy-profile comparison of the observed field morphology with a 2D radiation-MHD collapse simulation at 30 kyr  
  > "Figure [4](#model) presents qualitative and quantitative results from magneto-hydrodynamic cloud collapse simulations where gravity dominates over magnetic fields" (Discussion)
   - software: Pluto
   - parameter: 100 Msun core, 0.1 pc radius, r^-1.5 density slope, 4% rotational to gravitational energy, 10 K, mass-to-flux 20x critical  
  > "The core is initially in solid-body rotation with about 4% of rotational to gravitational energy, turbulent motions are neglected." (Simulations); "The initial temperature of the core is set to 10 K." (Simulations)
   - parameter: 56 radial x 10 polar grid cells, radial range 3 AU to 0.1 pc  
  > "The computational domain consists of 56 grid cells in the radial direction and 10 grid cells in the polar direction" (Simulations); "The dimension of the computational domain in the radial direction extends from 3 AU up to 0.1 pc." (Simulations)
   - assumption: Dust-to-gas mass ratio fixed to 1%; stellar radiative feedback and radiation forces neglected  
  > "The dust-to-gas mass ratio is fixed to 1% throughout the evolution of the system." (Simulations)
   - fitting: _not stated_
   - validation: Simulated field goes from centrally directed in the outer core to circular/toroidal in the inner disk, resembling the observed morphology  
  > "These simulations show field morphologies from a centrally directed pattern in the outer parts of the cloud core to a more circular pattern in the inner disk regions, resembling closely the observed morphology of the magnetic field" (Discussion)

## Software

- **CASA (pipeline)** 5.6.1: Calibration with the CASA pipeline following ALMA-provided scripts, and self-calibration  
  > "Calibration was done with the CASA pipeline version 5.6.1 following the ALMA provided calibration scripts." (Observations); "Self-calibration was applied within CASA improving especially the rms in the Stokes I continuum image by more than a factor 3." (Observations)
- **tclean** : Imaging Stokes I, Q, U and the 13CH3CN cube  
  > "We imaged the data with the tclean task in CASA experimenting with different robust parameters." (Observations)
- **Pluto** 4.1: MHD code for the comparison collapse simulation  
  > "we make use of the open source MHD code *Pluto* (cite: mignone2007) version 4.1." (Simulations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Synthesized beam of final images (robust 0.5) | 1.16'' x 0.96'', PA 81.4 deg | not stated | arcsec, deg | 1 | resulting in a spatial resolution of $1.16''\times 0.96''$ (PA. 81.4 deg) |
| Stokes I continuum rms | 1.5 | not stated | mJy/beam | 1 | images are 1.5 mJy beam$^{-1}$ and 5 $\mu$Jy beam$^{-1}$, respectively. |
| Linearly polarized intensity P rms | 5 | not stated | uJy/beam | 2 | images are 1.5 mJy beam$^{-1}$ and 5 $\mu$Jy beam$^{-1}$, respectively. |
| Brightness temperature at central peak (Rayleigh-Jeans, Stokes I) | ~44 | not stated | K | 2 | While the central peak position reaches a brightness temperature of $\sim$44 K, the mean temperature of the entire central core is $\sim$3.1 K. |
| Mean brightness temperature of the central core | ~3.1 | not stated | K | 2 | While the central peak position reaches a brightness temperature of $\sim$44 K, the mean temperature of the entire central core is $\sim$3.1 K. |
| Flux density of central source C (Stokes I, within 3 sigma contour) | 9.81 | not stated | Jy | 4 | 9.81 |
| Peak intensity of central source C | 1.966 | not stated | Jy/beam | 4 | 1.966 |
| Mass of central source C (Table 1) | 435 | +485/-223 (factor 2 in temperature) | Msun | 4 | $435^{+485}_{-223}$; The error margins for $M$ and $N$ correspond to an uncertainty of a factor 2 in the temperature. |
| Mass of central gravitational attractor (text) | roughly 400 | factor ~2 (T), up to factor 4 with kappa | Msun | 4 | the central gravitational attractor contains roughly 400 M$_{\odot}$ |
| Gas column density of C | 13.4 | +15.0/-6.9 | 1e24 cm^-2 | 4 | $13.4^{+15.0}_{-6.9}$ |
| Mass of NE1 (Table 1) | 9.2 | +10.3/-4.7 | Msun | 4 | $9.2^{+10.3}_{-4.7}$ |
| Mass of NE2 (Table 1) | 4.0 | +4.4/-2.1 | Msun | 4 | $4.0^{+4.4}_{-2.1}$ |
| Masses of the two filamentary substructures (text) | ~2.7 and ~1.5 | not stated | Msun | 4 | the two filamentary sub-structures are far less massive around $\sim$2.7 and $\sim$1.5 M$_{\odot}$ |
| Dust mass within 2'' (6200 AU) of the center | ~331 | not stated | Msun | 5 | we find approximately 331 M$_{\odot}$ |
| Centrifugal-equilibrium velocity at r = 6200 AU | 6.9 | not stated | km/s | 5 | How do these 6.9 km s$^{-1}$ compare to our observations? |
| Inclination consistent with observed velocities (0 = face-on) | ~9 | not stated | deg | 5 | With $i\sim 9$ deg, the required velocity $v$ is consistent with our observed velocities. |
| Level of the structure function at scales beyond ~1'' | ~52 | not stated | deg | 6 | the derived structure function is almost flat at an angle value of $\sim$52 deg at scales beyond $\sim$1$''$, which is consistent with a random distribution. |

## Qualitative findings

- In the outer parts the magnetic field points radially toward the gravitational center of the region from almost all azimuthal directions  
  > "it is intriguing that this magnetic field structure is oriented radially toward the center of the main Stokes $I$ emission peak from almost all azimuthal directions." (Morphologies and kinematics)
- The field in the NE filament is bent into a U shape directed toward the central continuum peak  
  > "the magnetic field is bent in a U-like shape, also directed radially toward the center of the main mm continuum peak." (Morphologies and kinematics)
- The 13CH3CN first-moment map shows a velocity gradient across the center, interpreted as possible rotation, where the field turns away from radial  
  > "one sees a velocity gradient from red- to blue-shifted from the north-west toward the south east." (Morphologies and kinematics)
- HRO: field mostly perpendicular to isophotes at large radii, becoming random toward the center  
  > "Getting close to the center, the orientation between magnetic field and contours becomes less perpendicular and again consistent with a random distribution." (Histogram of Relative Orientations (HRO))

## Claim tuples

- H: Does gravity shape the field on core scales in G327.3? | E: Mapped 1.3 mm polarized dust emission (Q, U) and rotated angles by 90 deg to trace B | R: Field is oriented radially toward the center of the main Stokes I peak from almost all azimuths; HRO shows B perpendicular to isophotes at large radii | F: The field is dragged toward the gravitational center | **supported**
- H: Do the filaments feeding the core carry gravity-dragged field? | E: Examined the field along the NE1/NE2 filament and the HRO phi map | R: U-shaped field directed toward the central peak; low phi (parallel) channels along the filament spines | F: Filaments show gravity-driven convergent flow signatures | **supported**
- H: Does rotation reshape the field in the inner ~2'' (~6200 AU)? | E: 13CH3CN moment-1 map, centrifugal-velocity estimate with 331 Msun, HRO V and phi inside the center | R: Velocity gradient, field no longer radial, HRO consistent with random inside; required 6.9 km/s consistent with observed ~1 km/s only for i ~ 9 deg | F: Rotation likely dominates the field morphology in the center, potentially tracing an embedded disk, but the system must be near face-on and magnetic braking is degenerate with inclination | **partially**
- H: Is the observed morphology consistent with gravity-dominated collapse of a weak-field core? | E: Compared the maps with a 2D radiation-MHD simulation of a 100 Msun core with mass-to-flux 20x critical | R: Simulation gives centrally directed field in the outer core and toroidal field in the disk, qualitatively resembling the observations | F: Suggestive of a weak-field scenario, but a pole-on view cannot exclude an hourglass with strong-field initial conditions | **partially**
- H: Can the field strength be measured with the DCF method? | E: Checked DCF assumptions and the structure function of polarization angles | R: Angle dispersion is not small and the structure function is flat at ~52 deg beyond ~1'' | F: DCF is not properly applicable, so energy terms cannot be compared | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Robust 0.5 chosen to optimize polarized sensitivity; HRO used because field strength cannot be estimated  
  > "To optimize for the sensitivity of the polarized emission in Stokes Q and U, the final data products presented here were imaged with a robust parameter of 0.5" (Observations); "Since we cannot properly estimate the magnetic field strength, a quantitative comparison of the corresponding energy terms is not possible." (Histogram of Relative Orientations (HRO))
- Alternative: Davis-Chandrasekhar-Fermi field-strength estimate rejected because the angle dispersion is not small  
  > "Since this is obviously not given in the region investigated here, the Davis-Chandrasekhar-Fermi method is not properly applicable." (Masses, column densities and magnetic field strengths)
- Alternative: Second-order structure function estimates of the turbulent-to-mean-field ratio judged unreliable  
  > "would not be reliable in this region." (Masses, column densities and magnetic field strengths)
- Alternative: Polarization fraction map not shown because of Stokes I line contamination  
  > "Because of the line contamination of the Stokes I data, we refrain from showing a polarization fraction map." (Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Stokes I continuum is overestimated by line contamination  
  > "While that results in an overestimation of the Stokes $I$ continuum emission" (Observations)
- Limitation (authors): Masses are rough estimates, uncertain by up to a factor 4  
  > "Adding a factor 2 uncertainty for the dust absorption coefficient, the mass uncertainty can be as high as a factor 4." (Masses, column densities and magnetic field strengths)
- Limitation (authors): Unresolved multiplicity and substructure below ~3000 AU may affect kinematics and polarization  
  > "Multiplicity and other potential substructure below our resolution limit ($\sim$3000 AU) may influence the kinematic and polarization observations." (Morphologies and kinematics)
- Limitation (authors): Pole-on geometry prevents excluding an hourglass morphology  
  > "However, the pole-on orientation does not allow us to exclude an hourglass-like morphology with strong-field initial conditions." (Conclusions)
- Caveat (inferred, ours): Text and Table 1 disagree on the filament masses (about 2.7 and 1.5 Msun in the text vs 9.2 and 4.0 Msun in Table 1) and slightly on C (400 vs 435 Msun)
- Caveat (inferred, ours): Assumed 100 K dust temperature is hard to reconcile with the quoted 44 K peak brightness temperature and optically-thin, line-contaminated Stokes I; mass of the central core is therefore model dependent
- Caveat (inferred, ours): The 9 deg inclination is inferred from a one-number velocity argument and is degenerate with magnetic braking
- Caveat (inferred, ours): Simulation is a 2D, low-resolution run of a 100 Msun core, much smaller than the observed ~400 Msun core, and is compared only qualitatively with the data
- Caveat (inferred, ours): HRO bin choices, uncertainties and significance thresholds are not given in the text
- Caveat (inferred, ours): Polarization beyond the inner third of the primary beam rests on an external recipe (Beuther 2018, Hull 2020) from a single pointing

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: tclean parameters (image/cell size, masks, thresholds, deconvolver)
- Missing: Self-calibration solution intervals and rounds
- Missing: Polarization calibration and Q/U imaging specifics
- Missing: HRO bin structure, smoothing and gradient computation
- Missing: Aperture and contour definitions for the mass table
- Missing: Simulation input files and the analysis that produced Figure 4
- Missing: Statement that data are public or product versions used
- Data volume (inferred): Three 1.3 mm polarization EBs with ~42 antennas and 4 spectral windows: likely on the order of 100-300 GB raw, tens of GB for calibrated measurement sets (inferred, not stated in the paper)
- Score (inferred): 3/5, Project code, calibrators, spectral setup, CASA version, robust value and the mass recipe (T, kappa, gas-to-dust, distance) are given and numbers are reported; but self-calibration, tclean masking/size, polarization calibration details and HRO settings are missing, and the two masses disagree between text and table.
- Rediscovery candidate: no, The paper does not state that the data are public and key polarization imaging and HRO settings are unspecified, so a faithful redo of the polarization and HRO results is not possible; the dust mass numbers could be approximated from the continuum alone.

## Links

- Method: (cite: dallolio2019) (Polarization de-biasing and sigma_P definition)
- Method: (cite: beuther2018; hull2020) (Combining nearby pointings so polarization is reliable beyond the inner 1/3 of the primary beam)
- Method: (cite: soler2013; soler2016; soler2019b) (Histogram of relative orientations method)
- Method: (cite: koelligan2018; kuiper2018) (Basis of the comparison collapse simulation)
- Companion: (cite: beuther2009c) (Earlier NH3(5,5) study showing a rotating central structure in G327.3 and the 100 K hot-core temperature)
- Companion: (cite: koch2018) (Comparison HRO/phi-map study of other cores)
- Related: ALMA cycle 6 project 2018.1.01449.S

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
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 78,
  "rate": 0.722
 },
 "evidence_ok": true
}
```
