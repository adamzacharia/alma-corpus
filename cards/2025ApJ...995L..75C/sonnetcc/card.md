# A Bridge between Young Stars Formed by Gravitational Interaction

`2025ApJ...995L..75C` | The Astrophysical Journal Letters 2025 | first author: Choi, Youngwoo | arXiv: 2512.14299 | DOI: 10.3847/2041-8213/ae279e

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Whether L1448 IRS3A and IRS3B underwent a recent gravitational flyby, tested with ALMA Band 7 continuum and line data plus SPH and radiative transfer simulations  
  > "In this Letter, we investigate the flyby between L1448 IRS3A and L1448 IRS3B." (Introduction)
- Target **L1448 IRS3A**: coordinates _not stated_; z/distance approximately 300 pc (L1448 region, Perseus)  
  > "L1448 IRS3 is located in the L1448 region of the Perseus molecular cloud at a distance of approximately 300 pc" (Introduction); distance from Ortiz_2018; Zucker_2018  
  > "L1448 IRS3 is located in the L1448 region of the Perseus molecular cloud at a distance of approximately 300 pc" (Introduction)
- Target **L1448 IRS3B**: coordinates _not stated_; z/distance approximately 300 pc (L1448 region, Perseus)  
  > "L1448 IRS3 is located in the L1448 region of the Perseus molecular cloud at a distance of approximately 300 pc" (Introduction); distance from Ortiz_2018; Zucker_2018  
  > "L1448 IRS3 is located in the L1448 region of the Perseus molecular cloud at a distance of approximately 300 pc" (Introduction)

## Data provenance

- ALMA projects: 2016.1.01520.S
- bands: Band 7 (870 um dust continuum), Cycle 4  
  > "L1448 IRS3 was observed with ALMA Band 7 during Cycle 4 (2016.1.01520.S, PI: John Tobin)." (2.1 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-6 (extended) and C40-3 (compact) observed; only C40-3 used here  
  > "The observations include two array configurations: an extended configuration (C40-6), which provides high angular resolution, and a compact configuration (C40-3), which is more sensitive to large-scale structures." (2.1 Observations); "In this study, we use only the compact configuration (C40-3) data" (2.1 Observations)
- baselines: _not stated_
- angular resolution: synthesized beam 0.758 x 0.442 arcsec, PA -15.7 deg (continuum)  
  > "The synthesized beam size is $0.758^{\prime\prime} \times 0.442^{\prime\prime}$ with a position angle (PA) of $-15.7^{\circ}$." (2.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.3 mJy/beam  
  > "has an rms noise level of 0.3 mJy beam$^{-1}$" (2.1 Observations)
- time on source: _not stated_
- observing dates: C40-6: 2016 October 1 and 4; C40-3: 2016 December 19  
  > "The extended configuration observations were carried out on 2016 October 1 and 4, while the compact configuration observations were conducted on 2016 December 19." (2.1 Observations)
- pi or archival as stated: PI John Tobin (2016.1.01520.S); data previously published by Reynolds et al. 2021  
  > "(2016.1.01520.S, PI: John Tobin)" (2.1 Observations); "The data were originally published in a previous study that revealed a prominent spiral structure in the L1448 IRS3B disk (cite: Reynolds_2021)." (2.1 Observations)
- Line: CO J = 3-2 (not analyzed here) (not stated)
- Line: C17O J = 3-2 (not stated)
- Line: H13CO+ J = 4-3 (not stated)
- Line: H13CN / SO2 (blended) H13CN J = 4-3 / SO2 13(2,12)-12(1,11) (not stated)
- Line: SiO J = 8-7 (not analyzed here) (not stated)
- External data: IRS3A protostellar mass 1.4 Msun from previous kinematic analysis  
  > "For IRS3A, we adopt a central protostellar mass of 1.4 $M_{\odot}$, based on previous kinematic analysis" (2.2 Hydrodynamical Simulations) [from (cite: Reynolds_2021; Gieser_2024)]
- External data: IRS3B inner binary combined mass 1.15 Msun; IRS3B-c below ~0.2 Msun  
  > "In IRS3B, the combined mass of the inner binary is 1.15 $M_{\odot}$" (2.2 Hydrodynamical Simulations); "roughly estimated to be below 0.2 $M_{\odot}$" (2.2 Hydrodynamical Simulations) [from (cite: Reynolds_2021)]
- External data: Initial disk masses 0.04 Msun (IRS3A) and 0.3 Msun (IRS3B) from earlier dust continuum fluxes, gas-to-dust 100  
  > "based on previous dust continuum flux measurements assuming a gas-to-dust ratio of 100" (2.2 Hydrodynamical Simulations) [from (cite: Tobin_2016; Reynolds_2021)]
- External data: Stellar effective temperatures from 1 Myr isochrones  
  > "The effective temperatures of the stellar components are estimated using 1 Myr isochrones." (3.1 Hydrodynamical Simulation) [from (cite: Siess_2000)]
- External data: Distance of about 300 pc  
  > "at a distance of approximately 300 pc" (Introduction) [from (cite: Ortiz_2018; Zucker_2018)]
- Simulation/model as data: PHANTOM SPH flyby runs: Run 1 without and Run 2 with an embedded source (50 MJ at 300 au in IRS3B disk)  
  > "We performed two simulations with and without the embedded source." (2.2 Hydrodynamical Simulations)
- Simulation/model as data: MCFOST synthetic 870 um continuum images and CO moment 1 map from simulation snapshots  
  > "We use the radiative transfer code `MCFOST` to generate synthetic observational images from the simulation snapshots" (3.1 Hydrodynamical Simulation)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.0  
  > "The raw data were calibrated and imaged using the Common Astronomy Software Applications (CASA) package version 4.7.0." (2.1 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0238+1636 (gain J0336+3218, bandpass J0237+2848)  
  > "The gain, bandpass, and flux calibrators used were J0336+3218, J0237+2848, and J0238+1636, respectively." (2.1 Observations)
- flux scale uncertainty: _not stated_
- self calibration: phase-only on continuum, solution intervals infinite and 60 s; solutions applied to continuum and line data  
  > "Phase-only self-calibration was performed on the dust continuum data with an infinite and a 60 s solution interval." (2.1 Observations); "The resulting phase solutions were applied to both the continuum and spectral line data" (2.1 Observations)

### Imaging

- task: CASA tclean (continuum and lines)  
  > "Continuum imaging was conducted using the CASA task" (2.1 Observations); "Molecular line imaging was also carried out with" (2.1 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5 (lines use the same weighting scheme)  
  > "with Briggs weighting and a robust parameter of 0.5" (2.1 Observations); "using the same weighting scheme as the continuum" (2.1 Observations)
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
- final beam: 0.758 x 0.442 arcsec, PA -15.7 deg (continuum)  
  > "The synthesized beam size is $0.758^{\prime\prime} \times 0.442^{\prime\prime}$ with a position angle (PA) of $-15.7^{\circ}$." (2.1 Observations)
- final rms: 0.3 mJy/beam (continuum)  
  > "has an rms noise level of 0.3 mJy beam$^{-1}$" (2.1 Observations)

### Inherited from earlier work

- The observations were originally published earlier; the H13CN/SO2 blend is taken from that work  
  > "The H$^{13}$CN line is blended with the SO$_2$ line (cite: Reynolds_2021)." (2.1 Observations) [from (cite: Reynolds_2021)]
- PHANTOM built-in flyby setup used for the orbit  
  > "We use the built-in flyby setup provided in the `PHANTOM` repository." (2.2 Hydrodynamical Simulations) [from PHANTOM (cite: Price_2018)]
- IRS3A mass 1.4 Msun adopted from earlier kinematic analysis  
  > "we adopt a central protostellar mass of 1.4 $M_{\odot}$, based on previous kinematic analysis" (2.2 Hydrodynamical Simulations) [from (cite: Reynolds_2021; Gieser_2024)]
- Initial disk masses from earlier dust continuum flux measurements  
  > "based on previous dust continuum flux measurements assuming a gas-to-dust ratio of 100" (2.2 Hydrodynamical Simulations) [from (cite: Tobin_2016; Reynolds_2021)]
- MCFOST radiative transfer setup follows earlier MCFOST papers  
  > "to generate synthetic observational images from the simulation snapshots (cite: Pinte_2006; Pinte_2009; Tessore_2021)" (3.1 Hydrodynamical Simulation) [from (cite: Pinte_2006; Pinte_2009; Tessore_2021)]

### Not stated but needed to reproduce (our reading)

- Which of the archival C40-3 execution blocks and spectral windows were used, and whether pipeline or manual calibration was run
- Image size, cell size, deconvolver, masking and cleaning threshold for continuum and line tclean runs
- Channel width, velocity range and any continuum subtraction or line-free channels for the line cubes
- Clipping thresholds used to make the moment 0 and moment 1 maps
- How the bridge length and width were measured (contour level, profile cut)
- Whether the IRS3A and IRS3B disks and the embedded source are set up with the same temperature profile, scale height and q in PHANTOM
- Snapshot selection and time offset for matching Run 1 and Run 2 to observations
- MCFOST inclination, position angle, dust composition, gas-to-dust and image grid for the synthetic maps
- Pixel position, rotation and mass-conversion details behind the Run 2 accretion rate curves
- Spectral line rest frequencies and the CASA flux-density scale applied

## Analysis recipe

1. **Calibrate and self-calibrate compact-array data**: CASA 4.7.0 calibration; phase-only self-calibration on continuum with infinite and 60 s solution intervals, applied to continuum and line data  
  > "The raw data were calibrated and imaged using the Common Astronomy Software Applications (CASA) package version 4.7.0." (2.1 Observations); "Phase-only self-calibration was performed on the dust continuum data with an infinite and a 60 s solution interval." (2.1 Observations)
   - software: CASA 4.7.0
   - parameter: solution intervals: infinite and 60 s  
  > "with an infinite and a 60 s solution interval" (2.1 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image the 870 um continuum**: tclean with Briggs weighting, robust = 0.5  
  > "with Briggs weighting and a robust parameter of 0.5" (2.1 Observations)
   - software: CASA tclean
   - parameter: beam 0.758 x 0.442 arcsec, PA -15.7 deg; rms 0.3 mJy/beam  
  > "The synthesized beam size is $0.758^{\prime\prime} \times 0.442^{\prime\prime}$ with a position angle (PA) of $-15.7^{\circ}$." (2.1 Observations); "has an rms noise level of 0.3 mJy beam$^{-1}$" (2.1 Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Image molecular lines and make moment maps**: tclean with the same weighting as continuum; moment 0 and moment 1 maps of H13CO+ 4-3, C17O 3-2 and H13CN/SO2  
  > "Molecular line imaging was also carried out with" (2.1 Observations); "using the same weighting scheme as the continuum" (2.1 Observations); "Integrated intensity (moment 0) and intensity-weighted velocity (moment 1) maps for the H$^{13}$CO$^{+}$ ($J$ = 4 → 3), C$^{17}$O ($J$ = 3 → 2)" (2.1 Observations)
   - software: CASA tclean
   - fitting: _not stated_
   - validation: _not stated_
4. **Characterize the bridge and spiral features in continuum and lines**: Visual identification in the 870 um image; bridge length and width quoted as projected sizes; line velocities used to infer the geometry  
  > "The length of the bridge is approximately $6^{\prime\prime}$ (projected length of 1800 AU), and the width is about $0.8^{\prime\prime}$ (projected width of 240 AU)." (3.1 Dust Continuum)
   - assumption: distance of approximately 300 pc  
  > "at a distance of approximately 300 pc" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
5. **Run SPH flyby simulations of IRS3A and IRS3B**: PHANTOM SPH with two disks and sink particles; IRS3A as perturber on a parabolic orbit around IRS3B; Run 1 without and Run 2 with an embedded 50 MJ source  
  > "In the simulations, L1448 IRS3A is modeled as the perturber on a parabolic orbit around L1448 IRS3B." (2.2 Hydrodynamical Simulations); "We performed two simulations with and without the embedded source." (2.2 Hydrodynamical Simulations)
   - software: PHANTOM
   - parameter: 5e5 gas SPH particles; sink radius 0.5 au  
  > "The two disks are modeled with $5 \times 10^{5}$ gas SPH particles" (2.2 Hydrodynamical Simulations); "The sink radius is set to 0.5 au for all sink particles." (2.2 Hydrodynamical Simulations)
   - parameter: Sigma proportional to R^-1; alpha_ss = 0.005  
  > "Both disks initially follow a power-law surface density profile of $\Sigma \propto R^{-1}$, and we adopt a Shakura–Sunyaev disk viscosity parameter of $\alpha_{\mathrm{ss}} = 0.005$." (2.2 Hydrodynamical Simulations)
   - parameter: pericenter 1500 au; initial separation 10 r_peri (3 r_peri in Run 2); node PA 15 deg, inclination 90 deg  
  > "The pericenter distance is set to $r_{\mathrm{peri}} = 1500$ au, and the initial separation between the two stars is 10 times the pericenter distance." (2.2 Hydrodynamical Simulations); "These are set to 15$^{\circ}$ and 90$^{\circ}$, respectively." (2.2 Hydrodynamical Simulations)
   - parameter: 180 deg rotation about the z-axis applied to match observed morphology  
  > "To reproduce the observed morphology, we apply a 180$^{\circ}$ rotation of the system around the $z$-axis, corresponding to the line-of-sight direction." (2.2 Hydrodynamical Simulations)
   - assumption: gas self-gravity neglected  
  > "Specifically, only sink–sink and gas–sink gravitational interactions are considered, while gas–gas self-gravity is neglected." (2.2 Hydrodynamical Simulations)
   - assumption: gas-to-dust ratio 100 for disk masses  
  > "based on previous dust continuum flux measurements assuming a gas-to-dust ratio of 100" (2.2 Hydrodynamical Simulations)
   - fitting: No formal fit; orbit and disk parameters set by hand and judged by morphology  
  > "To reproduce the observed morphology, we apply a 180$^{\circ}$ rotation of the system around the $z$-axis, corresponding to the line-of-sight direction." (2.2 Hydrodynamical Simulations)
   - validation: Qualitative comparison of simulated bridge and spirals with observed morphology  
  > "The synthetic dust continuum image successfully reproduces three key observational features" (3.1 Hydrodynamical Simulation)
6. **Generate synthetic images from snapshots**: MCFOST dust temperature from heating by the two sinks, then ray-traced 870 um continuum image and CO moment 1 map  
  > "A synthetic 870 $\mu$m dust continuum image is generated using a ray-tracing technique" (3.1 Hydrodynamical Simulation); "An intensity-weighted velocity (moment 1) map is also created from the synthetic CO emission cube using the same snapshot." (3.1 Hydrodynamical Simulation)
   - software: MCFOST
   - parameter: 10^8 photons; Teff 4498 K (IRS3A), 4367 K (IRS3B)  
  > "To compute the dust temperature structure, we launch $10^{8}$ photons." (3.1 Hydrodynamical Simulation); "The resulting effective temperatures are 4498 K for IRS3A and 4367 K for IRS3B" (3.1 Hydrodynamical Simulation)
   - parameter: MRN grain size distribution, a_min = 0.03 um to a_max = 1 mm  
  > "The dust grain population follows a standard MRN distribution ($\mathrm{d}n(a) \propto a^{-3.5}$) with grain sizes ranging from $a_{\mathrm{min}} = 0.03$ $\mu$m to $a_{\mathrm{max}} = 1$ mm." (3.1 Hydrodynamical Simulation)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compute accretion rates in Run 2**: Mass accretion rates of primary, perturber and embedded source tracked during the flyby simulation  
  > "we calculated the mass accretion rates of the system components" (3.1 Hydrodynamical Simulation)
   - software: PHANTOM
   - assumption: embedded source mass assumed; accretion rate depends on assumed IRS3B-c mass  
  > "We note that the precise accretion rate depends on the assumed mass of IRS3B-c" (3.1 Hydrodynamical Simulation)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: calibration, self-calibration and tclean imaging  
  > "The raw data were calibrated and imaged using the Common Astronomy Software Applications (CASA) package version 4.7.0." (2.1 Observations)
- **PHANTOM** : SPH flyby simulations  
  > "using the smoothed particle hydrodynamics (SPH) code `PHANTOM` (cite: Price_2018)" (2.2 Hydrodynamical Simulations)
- **MCFOST** : radiative transfer and synthetic images  
  > "We use the radiative transfer code `MCFOST` to generate synthetic observational images from the simulation snapshots" (3.1 Hydrodynamical Simulation)
- **NumPy** : listed in Software section; specific use not stated  
  > "CASA (cite: CASA_2022), NumPy (cite: Harris_2020), Matplotlib (cite: Hunter_2007)" (Software)
- **Matplotlib** : listed in Software section; specific use not stated  
  > "CASA (cite: CASA_2022), NumPy (cite: Harris_2020), Matplotlib (cite: Hunter_2007)" (Software)
- **Astropy** : listed in Software section; specific use not stated  
  > "Astropy (cite: Astropy_2013; Astropy_2018; Astropy_2022), SciPy (cite: Virtanen_2020)" (Software)
- **SciPy** : listed in Software section; specific use not stated  
  > "Astropy (cite: Astropy_2013; Astropy_2018; Astropy_2022), SciPy (cite: Virtanen_2020)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum synthesized beam (major x minor, PA) | 0.758 x 0.442 arcsec, PA -15.7 deg | not stated | arcsec, deg | 2 | The synthesized beam size is $0.758^{\prime\prime} \times 0.442^{\prime\prime}$ with a position angle (PA) of $-15.7^{\circ}$. |
| Continuum rms noise | 0.3 | not stated | mJy/beam | 2 | has an rms noise level of 0.3 mJy beam$^{-1}$ |
| Bridge projected length | approximately 6 arcsec (1800 AU) | not stated | arcsec; AU | 4 | The length of the bridge is approximately $6^{\prime\prime}$ (projected length of 1800 AU) |
| Bridge projected width | about 0.8 arcsec (240 AU) | not stated | arcsec; AU | 4 | the width is about $0.8^{\prime\prime}$ (projected width of 240 AU) |
| Angle beta between perturber orbit and IRS3B disk angular momentum | approximately 52 | not stated | deg | 5 | is calculated to be approximately 52$^{\circ}$, corresponding to a prograde flyby |
| Time of closest approach in Run 1 | t = 0.094 | not stated | Myr | 5 | following the closest approach ($t=0.094$ Myr) |
| Time since closest approach at the matched snapshot | 15,736 | not stated | yr | 5 | presents the simulation snapshot 15,736 yr after the closest approach ($t=0.11$ Myr) |
| Effective temperature of IRS3A | 4498 | not stated | K | 6 | The resulting effective temperatures are 4498 K for IRS3A and 4367 K for IRS3B |
| Effective temperature of IRS3B | 4367 | not stated | K | 6 | The resulting effective temperatures are 4498 K for IRS3A and 4367 K for IRS3B |
| Run 2 embedded source mass and orbital radius at current epoch | ~0.1 Msun and 250 au | not stated | Msun; au | 7 | The mass and orbital radius evolve to $\sim$0.1 $M_{\odot}$ and 250 au at the estimated current epoch. |

## Qualitative findings

- A long narrow dust bridge connects IRS3A and IRS3B, consistent with a recent prograde flyby  
  > "Strikingly, L1448 IRS3A and L1448 IRS3B are connected by a long, narrow bridge-like dust structure." (3.1 Dust Continuum)
- A fainter redshifted minor bridge connects to the east side of IRS3A, indicating IRS3A is in the foreground  
  > "This suggests that L1448 IRS3A is located in the foreground relative to L1448 IRS3B along the line of sight." (3.2 Molecular Lines)
- H13CN/SO2 emission is concentrated toward IRS3A  
  > "The H$^{13}$CN/SO$_{2}$ emission is concentrated around L1448 IRS3A and is not prominent in the L1448 IRS3B disk." (3.2 Molecular Lines)

## Claim tuples

- H: IRS3A and IRS3B have recently interacted through a flyby | E: ALMA Band 7 870 um continuum imaging of the compact-array data | R: A bridge about 6 arcsec (1800 AU) long and 0.8 arcsec wide links the two systems, alongside known spiral arms | F: The bridge and spirals indicate a recent prograde flyby | **supported**
- H: Molecular lines show kinematic signatures of the interaction | E: Moment 0 and 1 maps of H13CO+ 4-3, C17O 3-2 and H13CN/SO2 | R: Main bridge blueshifted and a fainter minor bridge redshifted, with H13CN/SO2 concentrated at IRS3A | F: Gas flows from IRS3B toward IRS3A, and IRS3A is in the foreground; SO2 origin would imply energetic perturbation | **partially**
- H: A prograde flyby reproduces the observed morphology and gives its timing | E: PHANTOM SPH Run 1 with MCFOST synthetic 870 um image and CO moment 1 map | R: Bridge, IRS3B spiral arm and IRS3A large-scale spiral reproduced; minor bridge and eastward arm not reproduced | F: Closest approach occurred about 15,000 yr ago | **partially**
- H: An embedded source in the IRS3B disk affects the flyby outcome and explains the IRS3B substructure | E: Run 2 with a 50 MJ source at 300 au and accretion rate calculation | R: Distinctive spiral substructures resembling observations; embedded source keeps the highest accretion rate | F: A flyby involving an embedded source can explain the IRS3B spirals and the bright compact structure around IRS3B-c | **supported**

## Reasoning

- Why this data: Compact C40-3 data chosen for sensitivity to large-scale structure despite lower resolution  
  > "which offers enhanced sensitivity to large-scale structures, despite its lower spatial resolution" (2.1 Observations)
- Why this method: Run 2 initial separation reduced to 3 r_peri so the embedded source does not alter the disk before the flyby  
  > "The Run 2 simulation adopted an initial separation of $3\,r_{\rm peri}$ to minimize the impact of the embedded source on the disk before the flyby interaction." (Table 1)
- Alternative: IRS3B spirals might have pre-existed the flyby via gravitational instability, though the flyby may have shaped them  
  > "The spiral structures observed in the L1448 IRS3B disk might have existed before the flyby with L1448 IRS3A" (3.1 Hydrodynamical Simulation)
- Alternative: CO and SiO outflow and jet data not analyzed since they show no flyby signature  
  > "As we do not find any clear signatures of flyby interactions in the jet or outflow structures traced by CO ($J$ = 3 → 2) and SiO ($J$ = 8 → 7) observations, they are not analyzed in this Letter." (2.1 Observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas self-gravity is neglected, which may explain discrepancies  
  > "The discrepancies between the observations and simulations may result from the neglect of self-gravity." (2.2 Hydrodynamical Simulations)
- Limitation (authors): The simulation omits the dense ambient envelope material  
  > "our simulation includes only the circumstellar disks of the two systems" (3.1 Hydrodynamical Simulation)
- Limitation (authors): Simulation gives almost no line-of-sight velocity difference between IRS3A and IRS3B, unlike the observed 0.5 km/s  
  > "the simulation yields almost no line-of-sight velocity difference" (3.1 Hydrodynamical Simulation)
- Limitation (authors): IRS3B-c mass is poorly constrained, affecting the accretion rate  
  > "the mass of the tertiary component (L1448 IRS3B-c) is not well constrained" (2.2 Hydrodynamical Simulations)
- Caveat (inferred, ours): Orbit and disk parameters were chosen by hand with no parameter search or uncertainty, so the 15,000 yr timing has no error bar
- Caveat (inferred, ours): H13CN/SO2 blend means the shock interpretation of the IRS3A emission is conditional
- Caveat (inferred, ours): Run 2 uses a different initial separation than Run 1, so the runs are not directly comparable
- Caveat (inferred, ours): Observational structures (minor bridge, eastward arm) are not reproduced, so the single-flyby model is incomplete
- Caveat (inferred, ours): Bridge length and width are quoted without a stated measurement method or uncertainty

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: PHANTOM flyby setup is part of the public PHANTOM repository; no paper-specific input files stated  
  > "We use the built-in flyby setup provided in the `PHANTOM` repository." (2.2 Hydrodynamical Simulations)
- Missing: Image and cell size, masking, deconvolver and clean threshold for tclean
- Missing: Spectral window and channel settings for the line cubes and moment-map clipping
- Missing: PHANTOM setup file values not listed in Table 1 (disk temperature and aspect ratio, snapshot output times)
- Missing: MCFOST viewing geometry, dust composition and image settings
- Missing: Bridge measurement method
- Data volume (inferred): Roughly tens of GB for the C40-3 execution blocks of the Band 7 project; simulations add a few GB of PHANTOM dumps
- Score (inferred): 3/5, Project code and key imaging settings (CASA 4.7.0, robust 0.5, self-cal intervals) and full simulation setup are given, but cell size, masks, channels, moment thresholds and MCFOST geometry are missing, and results are mostly qualitative with few numbers.
- Rediscovery candidate: no, The ALMA project code is given and the simulation recipe is largely listed, but the main results are morphological and qualitative rather than numeric, and several imaging and radiative transfer settings are unstated.

## Links

- Method: Reynolds_2021 (Original publication of the 2016.1.01520.S data and source of masses and the H13CN/SO2 blend)
- Method: Price_2018 (PHANTOM SPH code)
- Method: Pinte_2006; Pinte_2009; Tessore_2021 (MCFOST radiative transfer code)
- Method: Siess_2000 (Isochrones for stellar effective temperatures)
- Companion: Tobin_2016 (High-resolution ALMA study of the IRS3B disk spirals and disk mass)
- Companion: Looney_2025 (ALMA Band 4 continuum showing the eastward arm and IRS3B spirals)
- Companion: Gieser_2024 (NOEMA bridge-like structure between IRS3A and IRS3B and IRS3A mass)
- Companion: Cuello_2019; Cuello_2020; Cuello_2023 (Flyby simulations predicting bridges and spiral arms)
- Related: ALMA 2016.1.01520.S (PI John Tobin)

## Checks

```json
{
 "quotes": 110,
 "quotes_ok": 110,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 108,
  "stated": 70,
  "rate": 0.648
 },
 "evidence_ok": true
}
```
