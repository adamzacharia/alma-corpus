# ATOMS-QUARKS Survey: Inflow and Infall in Massive Protocluster G318.049+00.086— Evidence of Competitive Accretion

`2026ApJ...999..180G` | The Astrophysical Journal 2026 | first author: Gupta, Shivani | arXiv: 2602.01238 | DOI: 10.3847/1538-4357/ae40fd

Card schema 1.0 | model gemini-3.8-flash | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: To understand the multi-scale gas dynamics, mass inflow along filaments, and gas infall onto embedded cores in the massive protocluster G318.049+00.086 to distinguish massive star formation scenarios.  
  > "In this paper, we studied the multi-scale gas dynamics of a massive protocluster (G318.049+00.086) that has reported evidence of the presence of multiple filaments and several prestellar and protostellar cores to understand the underlying star formation mechanism." (1 Introduction)
- Target **G318.049+00.086**: coordinates _not stated_; z/distance 2.90 +0.52/-0.47 kpc  
  > "The protocluster G318.049+00.086, also known as I14498-5856, is located at a distance of 2.90+0.52-0.47 kpc (cite: 2019ApJ...885..131R) and has a local standard of rest velocity (Vlsr) of -49.82 km s-1 (cite: 2021RAA....21...14Y)." (1.1 Selected region); distance from 2019ApJ...885..131R  
  > "The protocluster G318.049+00.086, also known as I14498-5856, is located at a distance of 2.90+0.52-0.47 kpc (cite: 2019ApJ...885..131R) and has a local standard of rest velocity (Vlsr) of -49.82 km s-1 (cite: 2021RAA....21...14Y)." (1.1 Selected region)

## Data provenance

- ALMA projects: 2019.1.00685.S, 2017.1.00545.S
- bands: Band 3 (3 mm), Band 6 (1.3 mm), Band 7 (870 µm)  
  > "Figure 1 represents the 3 mm (left panel) and 1.3 mm (right panel) dust continuum maps of the protocluster obtained from the ATOMS and QUARKS surveys, respectively" (1.1 Selected region); "Recently, (cite: 2024ApJS..270....9X) identified 16 dense cores in the protocluster using the 870 μm dust continuum map observed using the Atacama Large Millimeter/submillimeter Array" (1.1 Selected region)
- frequencies and spectral setup: H13CN (1–0) at 86.339918 GHz, H13CO+ (1–0) at 86.754288 GHz, CCH (1–0) at 87.316898 GHz, CS (2–1) at 97.980953 GHz, CH3OH (13_1,12–13_0,13) at 342.729781 GHz, H13CN (4–3) at 345.339760 GHz, 3 mm continuum at ~99.93 GHz  
  > "The 3 mm (∼99.93 GHz) dust continuum map having a beam size of 2.34″ × 2.16″ is constructed using data from line-free spectral channels." (2.1 ATOMS survey); "H13CN (1–0) 86.339918 0.424 2.34 × 2.16 11.3; H13CO+ (1–0) 86.754288 0.422 2.66 × 2.52 11.1; CCH (1–0) 87.316898 0.419 2.63 × 2.50 11.3; CS (2–1) 97.980953 2.973 2.36 × 2.18 5.0" (Table 1); "CH3OH (131,12–130,13) 342.729781 0.986 1.11 × 0.82 6.5; H13CN (4–3) 345.339760 0.980 1.08 × 0.80 6.3" (Table 1)
- continuum bandwidth: _not stated_
- arrays: 12-m array and 7-m ACA  
  > "Calibration of the 12-m array data and ACA data were done separately using the Common Astronomy Software Applications (CASA) package version 5.6 (cite: mcmullin2007asp), and subsequently the visibility data were combined and re-imaged" (2.1 ATOMS survey); "QUARKS also have ACA observations ((cite: 2024RAA....24f5011X), Quarks paper II). The combine data has MRS of ∼ 8.45″" (2.3 QUARKS survey)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.34″ × 2.16″ to 2.66″ × 2.52″ (ATOMS Band 3 lines/continuum); 1.08″ × 0.80″ to 1.11″ × 0.82″ (ASSEMBLE Band 7 lines); 0.40″ × 0.34″ (QUARKS 1.3 mm continuum)  
  > "mm continuum ... 2.34 × 2.16; H13CO+ (1–0) ... 2.66 × 2.52; CH3OH ... 1.11 × 0.82; mm continuum ... 0.40 × 0.34" (Table 1); "complementing the ATOMS survey with an improved angular resolution (∼ 0.3″)." (2.3 QUARKS survey)
- max recoverable scale: ~87″ (ATOMS 12m+ACA); ~8.45″ (ASSEMBLE 12m); ~8.45″ (QUARKS combine data)  
  > "The maximum recoverable scale (MRS) of 12m + ACA combine data reaches ∼ 87″ (cite: 2023MNRAS.520.3259X)." (2.1 ATOMS survey); "The MRS of this data is ∼ 8.45″ (cite: 2023MNRAS.520.3259X)." (2.2 ASSEMBLE survey); "The combine data has MRS of ∼ 8.45″ (cite: 2024RAA....24f5011X)." (2.3 QUARKS survey)
- sensitivity: 11.1 to 11.3 mJy beam-1 (ATOMS 3 mm lines), 5.0 mJy beam-1 (CS), 6.3 to 6.5 mJy beam-1 (ASSEMBLE lines), rms noise 0.27 K in line-free channels  
  > "H13CN (1–0) ... 11.3; H13CO+ (1–0) ... 11.1; CCH (1–0) ... 11.3; CS (2–1) ... 5.0; CH3OH ... 6.5; H13CN (4–3) ... 6.3" (Table 1); "The S/N ratio was calculated based on an rms noise level of 0.27 K, estimated from the line-free channels using FUNStools." (3.5 Gas infall rates in cores)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ATOMS PI: Tie Liu; ASSEMBLE PI: Tie Liu  
  > "survey named the ALMA three-millimeter observations of massive star-forming regions survey (ATOMS; Project ID: 2019.1.00685.S; PI: Tie Liu)." (2.1 ATOMS survey); "Massive Protoclusters with Blue Profiles (ASSEMBLE; Project ID: 2017.1.00545.S; PI: Tie Liu)." (2.2 ASSEMBLE survey)
- Line: H13CN (1–0) (86.339918 GHz)
- Line: H13CO+ (1–0) (86.754288 GHz)
- Line: CCH (1–0) F(2–1) (87.316898 GHz)
- Line: CS (2–1) (97.980953 GHz)
- Line: CH3OH (13_1,12–13_0,13) (342.729781 GHz)
- Line: H13CN (4–3) (345.339760 GHz)
- External data: Distance to G318.049+00.086 (2.90 +0.52/-0.47 kpc)  
  > "The protocluster G318.049+00.086, also known as I14498-5856, is located at a distance of 2.90+0.52-0.47 kpc (cite: 2019ApJ...885..131R)" (1.1 Selected region) [from 2019ApJ...885..131R]
- External data: Vlsr (-49.82 km/s), global infall velocity (3.77 km/s), and mass infall rate (1.56e4 Msun/Myr)  
  > "and has a local standard of rest velocity (Vlsr) of -49.82 km s-1 (cite: 2021RAA....21...14Y)." (1.1 Selected region); "Using the CO (4–3) line, (cite: 2021RAA....21...14Y) also reported that the global infall velocity and mass infall rate for this cluster to be Vin = 3.77 ± 0.07 km s-1 and M˙ in = (1.56 ± 0.03) × 104 M⊙ Myr-1." (1.1 Selected region) [from 2021RAA....21...14Y]
- External data: Protocluster mass (1023.3 Msun) and dust temperature (26.7 K)  
  > "The mass and dust temperature (Tdust) of the protocluster are 1023.3 M⊙ and 26.7 K, respectively (cite: 2018MNRAS.473.1059U)." (1.1 Selected region) [from 2018MNRAS.473.1059U]
- External data: 16 dense cores identified in 870 µm continuum, their physical parameters (mass, radius, temperature, surface density) and evolutionary classification  
  > "Recently, (cite: 2024ApJS..270....9X) identified 16 dense cores in the protocluster using the 870 μm dust continuum map observed using the Atacama Large Millimeter/submillimeter Array (ALMA; see their Figure 2b) and also derived several physical parameters" (1.1 Selected region) [from 2024ApJS..270....9X]
- External data: CO (3–2) bipolar outflows for core classification  
  > "Further, they also classified these cores as prestellar core candidates or protostellar cores based on their association with the bipolar outflows traced in the CO (3–2) line by (cite: 2020ApJ...890...44B)." (1.1 Selected region) [from 2020ApJ...890...44B]

## Processing

### Calibration

- pipeline or manual: Separate calibration of 12-m and ACA data using CASA  
  > "Calibration of the 12-m array data and ACA data were done separately using the Common Astronomy Software Applications (CASA) package version 5.6 (cite: mcmullin2007asp), and subsequently the visibility data were combined and re-imaged" (2.1 ATOMS survey)
- casa version: 5.6  
  > "using the Common Astronomy Software Applications (CASA) package version 5.6 (cite: mcmullin2007asp)" (2.1 ATOMS survey)
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
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: used for 3 mm and 1.3 mm continuum maps  
  > "The 3 mm (∼99.93 GHz) dust continuum map having a beam size of 2.34″ × 2.16″ is constructed using data from line-free spectral channels." (2.1 ATOMS survey); "The corresponding 1.3 mm dust continuum map is prepared from the available line-free spectral channels (cite: 2024RAA....24b5009L)." (2.3 QUARKS survey)
- primary beam correction: All images used in analysis are primary beam corrected  
  > "All the images used in our analysis are primary beam corrected." (2.1 ATOMS survey)
- array combination: 12m + ACA combined for ATOMS and QUARKS  
  > "and subsequently the visibility data were combined and re-imaged to recover the extended emission." (2.1 ATOMS survey); "The combine data has MRS of ∼ 8.45″ (cite: 2024RAA....24f5011X)." (2.3 QUARKS survey)
- smoothing: _not stated_
- final beam: 3 mm continuum: 2.34″ × 2.16″; H13CO+ (1–0): 2.66″ × 2.52″; CCH (1–0): 2.63″ × 2.50″; 1.3 mm continuum: 0.40″ × 0.34″  
  > "mm continuum ... 2.34 × 2.16; H13CO+ (1–0) ... 2.66 × 2.52; CCH (1–0) ... 2.63 × 2.50; mm continuum ... 0.40 × 0.34" (Table 1)
- final rms: H13CO+: 11.1 mJy beam-1; CCH: 11.3 mJy beam-1; CS: 5.0 mJy beam-1; CH3OH: 6.5 mJy beam-1; H13CN (4-3): 6.3 mJy beam-1; 0.27 K line rms  
  > "H13CN (1–0) ... 11.3; H13CO+ (1–0) ... 11.1; CCH (1–0) ... 11.3; CS (2–1) ... 5.0; CH3OH ... 6.5; H13CN (4–3) ... 6.3" (Table 1); "The S/N ratio was calculated based on an rms noise level of 0.27 K, estimated from the line-free channels using FUNStools." (3.5 Gas infall rates in cores)

### Inherited from earlier work

- FilFinder application to H13CO+ moment 0 map to identify filaments  
  > "(cite: 2022MNRAS.514.6038Z), as part of the ATOMS survey, identified filamentary structures in this protocluster by applying the Python-based FilFinder algorithm (cite: 2015MNRAS.452.3435K) on the moment-0 map of H13CO+ emission." (3.1 Identification of filaments) [from 2022MNRAS.514.6038Z]
- 16 cores, positions, masses, radii, surface densities, and classification into protostellar/prestellar  
  > "Recently, (cite: 2024ApJS..270....9X) identified 16 dense cores in the protocluster using the 870 μm dust continuum map observed using the Atacama Large Millimeter/submillimeter Array (ALMA; see their Figure 2b) and also derived several physical parameters" (1.1 Selected region) [from 2024ApJS..270....9X]
- Cylindrical mass inflow rate formula for filaments  
  > "To quantify the mass flow along the filaments, we followed a similar methodology described in (cite: 2013ApJ...766..115K)." (3.4 Mass inflow rate along the filaments) [from 2013ApJ...766..115K]
- Mass infall rate formula for cores from infall velocity and core size/mass  
  > "The estimated infall velocities were further used to derive the mass infall rate (M˙ in) of gaseous material following the equation (cite: 2001ApJS..136..703L; 2022ApJ...940..112K; 2025arXiv251116978M):" (3.5 Gas infall rates in cores) [from 2001ApJS..136..703L]

### Not stated but needed to reproduce (our reading)

- Imaging parameters for QUARKS and ATOMS (e.g. tclean cell size, robust parameter, number of iterations, masking scheme)
- Continuum subtraction method details for line cubes
- Specific parameter bounds and prior distributions for the Hill5 MCMC fitting

## Analysis recipe

1. **Identify filamentary structures and skeletons**: Applied the FilFinder algorithm on the moment-0 map of H13CO+ and on the 1.3 mm QUARKS continuum map to extract skeletons and branches.  
  > "(cite: 2022MNRAS.514.6038Z), as part of the ATOMS survey, identified filamentary structures in this protocluster by applying the Python-based FilFinder algorithm (cite: 2015MNRAS.452.3435K) on the moment-0 map of H13CO+ emission." (3.1 Identification of filaments); "We also employed the FilFinder algorithm to the 1.3 mm continuum map obtained in the QUARKS survey, as the continuum emission has good spatial resolution." (3.1 Identification of filaments)
   - software: FilFinder
   - parameter: _not stated_
   - assumption: Filament structures traced by continuum and H13CO+ coincide and trace dense gas pathways  
  > "We note that the longest filaments obtained from both the emissions strongly coincide with each other." (3.1 Identification of filaments)
   - fitting: _not stated_
   - validation: Comparison and overlay of skeletons derived from H13CO+ and 1.3 mm continuum  
  > "In Figure 2c, we overlay the filamentary structures obtained from H13CO+ and 1.3 mm continuum emission to examine their spatial correlation." (3.1 Identification of filaments)
2. **Derive column density and mass map of the protocluster**: Derived H13CO+ column density assuming LTE and optically thin emission, masked pixels with integrated intensity < 5sigma, and converted to N(H2) assuming [H13CO+/H2] = 10^-11.  
  > "To generate the map, we chose the H13CO+ line, and it was derived using the formula obtained under the assumption of local thermodynamic equilibrium and the emission is optically thin" (3.2 Column density map); "For the construction of the column density map (N(H13CO+)), we considered only the pixels with integrated intensity >5σ in the moment-0 map." (3.2 Column density map); "Thus, we derived the N(H2) from N(H13CO+) using the mean of the reported abundance ratio of 10-11." (3.2 Column density map)
   - parameter: J = 0, mu = 3.89 D, B = 43.377302 GHz, Tex = Tdust = 26.7 K, Tbg = 2.73 K, [H13CO+/H2] = 10^-11  
  > "For this H13CO+ (1–0) transition, we used J = 0, μ = 3.89 D, and B = 43.377302 GHz" (3.2 Column density map); "In this calculation, we assume that Tex is equal to the dust temperature of the clump (Tdust)." (3.2 Column density map)
   - assumption: LTE, optically thin H13CO+ emission, Tex equals Tdust, uniform abundance [H13CO+/H2] = 10^-11 across clump  
  > "under the assumption of local thermodynamic equilibrium and the emission is optically thin" (3.2 Column density map); "In this calculation, we assume that Tex is equal to the dust temperature of the clump (Tdust)." (3.2 Column density map)
   - fitting: _not stated_
   - validation: Assessed impact of opacity (tau = 0.5-1.5), temperature uncertainty (+/- 10 K), and abundance variations (10^-10 to 10^-12)  
  > "If we consider H13CO+ has a moderate opacity (τ ∼ 0.5-1.5), the optically thin assumption would underestimate the column density by a factor τ /(1 - e-τ)" (3.2 Column density map); "A plausible uncertainty of ±10 K to our adopted value introduces an uncertainty of approximately 33% to 36% in the derived N(H2)." (3.2 Column density map)
3. **Measure velocity gradients and mass inflow rates along filaments**: Constructed PV diagrams from H13CO+ centroid velocity along skeletons, performed least-squares linear fits to measure velocity gradients, and calculated mass inflow rate assuming a cylindrical flow model.  
  > "The PV diagrams of the filaments were constructed by determining the centroid velocity along each of these filament skeletons." (3.3 Dynamical properties of filaments); "For estimation of the velocity gradients, we performed least-square fits to different parts of the PV diagrams signifying the filaments" (3.3 Dynamical properties of filaments); "Assuming a simple cylindrical model, the equation for mass inflow rate of the axial flow motion can be written as M˙ ∥ = ∇V∥Mfil / tan α" (3.4 Mass inflow rate along the filaments)
   - parameter: tan(alpha) = 1 (inclination alpha = 45 deg)  
  > "The mass inflow rates along the filaments F1, F3 and F4 were computed using the estimated filament masses and the velocity gradients (see Table [tab:mass_aacretion]), and assuming the inclination angle (α) of 45◦" (3.4 Mass inflow rate along the filaments)
   - assumption: Cylindrical geometry, inclination angle alpha = 45 deg, steady axial mass flow  
  > "Assuming a simple cylindrical model, the equation for mass inflow rate of the axial flow motion can be written as" (3.4 Mass inflow rate along the filaments); "We thus assume tan α = 1 in our calculation, and the estimated velocity gradients and mass inflow rates are expected to be uncertain by a factor of 2 when the α changes between 30◦ and 60◦" (3.4 Mass inflow rate along the filaments)
   - fitting: Least-squares linear regression to determine slopes in PV diagrams  
  > "For estimation of the velocity gradients, we performed least-square fits to different parts of the PV diagrams signifying the filaments (see Figure 5). The slopes of these fits represent the mean velocity gradients." (3.3 Dynamical properties of filaments)
   - validation: Evaluated inclination uncertainty between 30 and 60 deg, and checked consistency with previous ATOMS measurements  
  > "and the estimated velocity gradients and mass inflow rates are expected to be uncertain by a factor of 2 when the α changes between 30◦ and 60◦" (3.4 Mass inflow rate along the filaments)
4. **Determine systemic velocity and infall velocity of dense cores**: Fit single Gaussian profiles to optically thin lines (CH3OH, H13CN 4-3) to measure Vlsr. Fit H13CO+ and CCH spectra with S/N >= 15 using the Hill5 radiative transfer model with MCMC sampling to derive infall velocities.  
  > "We fit Gaussians to the average spectra of these optically thin tracers to determine the Vlsr of each core." (3.5 Gas infall rates in cores); "The infall velocity of the cores with blue profile was determined by fitting the observed spectral profiles of H13CO+ and CCH with the Hill5 infall model (cite: 2005ApJ...620..800D)." (3.5 Gas infall rates in cores); "the fitting was performed by Markov Chain Monte Carlo (MCMC) sampling using the emcee Python package (cite: 2013ascl.soft03002F)." (8 Hill5 Model Fit to the Infall Profiles)
   - software: FUNStools, emcee
   - parameter: S/N threshold >= 15, rms noise level = 0.27 K  
  > "To reliably determine the infall velocity from the asymmetric line profiles using the Hill5 model, we applied a signal-to-noise (S/N) threshold ≳ 15 to the observed spectra. The S/N ratio was calculated based on an rms noise level of 0.27 K" (3.5 Gas infall rates in cores)
   - parameter: Five Hill5 free parameters: Tpeak, tau, Vinfall, VLSR, sigma  
  > "The optical depth of the core is τ , and its infall velocity is Vinfall, while the systematic velocity of the system is VLSR, and both the regions are assumed to have equal velocity dispersion of σ for the observed molecule. These five parameters were set as free" (8 Hill5 Model Fit to the Infall Profiles)
   - assumption: Two approaching layers with linearly increasing excitation temperature toward the center; equal velocity dispersion in both regions  
  > "The Hill5 model is a simple radiative transfer model used for deriving infall velocity in a contracting molecular cloud by dealing with radiative transfer processes in two approaching layers whose excitation temperatures linearly increase toward the inner region" (8 Hill5 Model Fit to the Infall Profiles)
   - fitting: MCMC sampling using emcee in two trials: initial trial with broad parameter range to locate probable region, second trial with refined bounds  
  > "the fitting was performed by Markov Chain Monte Carlo (MCMC) sampling using the emcee Python package (cite: 2013ascl.soft03002F). The corner plots were generated to check the posterior probability distributions of parameters for each spectrum." (8 Hill5 Model Fit to the Infall Profiles); "In the initial trial, we set the parameter range very broad to identify the most probable region across possible local minima. The second trial uses this result to set more reasonable bounds on the parameters for a final fit." (8 Hill5 Model Fit to the Infall Profiles)
   - validation: Examined corner plots of posterior distributions; checked consistency between H13CO+ and CCH fits where both were available (cores 10, 11, 12); discarded unreliable fits  
  > "Note that for cores where Vin is derived for both the tracers (cores 10, 11 and 12), the obtained values are found to be consistent with each other." (3.5 Gas infall rates in cores); "Fit to a few spectra (cores 7, 10, and 14 for H13CO+, and cores 5, 8, 9, 13, and 14 for CCH) were unreliable due to the complex nature of their spectra, and hence, they were excluded from further analysis." (3.5 Gas infall rates in cores)
5. **Calculate mass infall rates for cores and compare with filament inflow**: Calculated mass infall rate as M_dot_in = 3 * M_in / R_in * V_in using adopted core masses and radii.  
  > "The estimated infall velocities were further used to derive the mass infall rate (M˙ in) of gaseous material following the equation (cite: 2001ApJS..136..703L; 2022ApJ...940..112K; 2025arXiv251116978M): M˙ in = 3Min/Rin * Vin" (3.5 Gas infall rates in cores)
   - parameter: M_in and R_in adopted from Xu et al. (2024)  
  > "where Min is the core mass, and Rin is the core radius, adopted from (cite: 2024ApJS..270....9X)." (3.5 Gas infall rates in cores)
   - assumption: Uniform spherical core collapse model  
  > "following the equation (cite: 2001ApJS..136..703L; 2022ApJ...940..112K; 2025arXiv251116978M): M˙ in = 3Min/Rin * Vin" (3.5 Gas infall rates in cores)
   - fitting: _not stated_
   - validation: Compared core mass infall rates to filament inflow rates and tested mass growth timescales  
  > "Accumulation of a small fraction (∼20-30%) of inflowing gas (see Table [tab:mass_aacretion]) onto the individual core during this timescale may lead to a significant mass growth" (4.3 Possible evolution of the cores)

## Software

- **CASA** 5.6: Separate calibration of 12-m and ACA data, combining visibility data and imaging  
  > "Calibration of the 12-m array data and ACA data were done separately using the Common Astronomy Software Applications (CASA) package version 5.6 (cite: mcmullin2007asp), and subsequently the visibility data were combined and re-imaged" (2.1 ATOMS survey)
- **FilFinder** : Identification of filamentary structures and skeletons in H13CO+ moment-0 map and 1.3 mm continuum map  
  > "identified filamentary structures in this protocluster by applying the Python-based FilFinder algorithm (cite: 2015MNRAS.452.3435K) on the moment-0 map of H13CO+ emission." (3.1 Identification of filaments); "We also employed the FilFinder algorithm to the 1.3 mm continuum map obtained in the QUARKS survey" (3.1 Identification of filaments)
- **FUNStools** : Estimating rms noise level from line-free channels  
  > "The S/N ratio was calculated based on an rms noise level of 0.27 K, estimated from the line-free channels using FUNStools." (3.5 Gas infall rates in cores)
- **emcee** : Markov Chain Monte Carlo (MCMC) sampling for fitting the Hill5 infall model to observed line spectra  
  > "the fitting was performed by Markov Chain Monte Carlo (MCMC) sampling using the emcee Python package (cite: 2013ascl.soft03002F)." (8 Hill5 Model Fit to the Infall Profiles)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity gradient along filament F1 | 17.8 | 1.1 | km s-1 pc-1 | 3 | F1 / 0.07 / 99±33 / 1414±473 / 17.8±1.1 / 1762±598 |
| Velocity gradient along filament F3 | 22.1 | 2.0 | km s-1 pc-1 | 3 | F3 / 0.13 / 227±76 / 1746±585 / 22.1±2.0 / 5017±1735 |
| Velocity gradient along filament F4 | 10.9 | 0.8 | km s-1 pc-1 | 3 | F4 / 0.12 / 119±40 / 992±333 / 10.9±0.8 / 1297±445 |
| Mass inflow rate along filament F1 | 1762 | 598 | Msun Myr-1 | 3 | F1 / 0.07 / 99±33 / 1414±473 / 17.8±1.1 / 1762±598 |
| Mass inflow rate along filament F3 | 5017 | 1735 | Msun Myr-1 | 3 | F3 / 0.13 / 227±76 / 1746±585 / 22.1±2.0 / 5017±1735 |
| Mass inflow rate along filament F4 | 1297 | 445 | Msun Myr-1 | 3 | F4 / 0.12 / 119±40 / 992±333 / 10.9±0.8 / 1297±445 |
| Filament F1 mass | 99 | 33 | Msun | 2 | F1 / 0.07 / 99±33 |
| Filament F3 mass | 227 | 76 | Msun | 2 | F3 / 0.13 / 227±76 |
| Filament F4 mass | 119 | 40 | Msun | 2 | F4 / 0.12 / 119±40 |
| Core 5 infall velocity from H13CO+ | 1.05 | +0.12/-0.11 | km s-1 | 4 | 5 / 4.0±2.4 / 4550 / −50.61 / 1.05+0.12−0.11 / - / 54.9±35.1 |
| Core 7 infall velocity from CCH | 1.24 | +0.26/-0.27 | km s-1 | 4 | 7 / 9.7±5.2 / 3680 / −50.70 / - / 1.24+0.26−0.27 / - / 196.2±110.9 |
| Core 10 infall velocity from H13CO+ | -0.16 | +0.06/-0.07 | km s-1 | 4 | 10 / 6.0±4.1 / 3360 / −49.31 / −0.16+0.06−0.07 / −0.14+0.03−0.03 / −68.9±41.7 / −46.3±31.7 |
| Core 7 mass infall rate from CCH | 196.2 | 110.9 | 10-5 Msun yr-1 | 5 | 7 / 9.7±5.2 / 3680 / −50.70 / - / 1.24+0.26−0.27 / - / 196.2±110.9 |
| Core 5 mass infall rate from H13CO+ | 54.9 | 35.1 | 10-5 Msun yr-1 | 5 | 5 / 4.0±2.4 / 4550 / −50.61 / 1.05+0.12−0.11 / - / 54.9±35.1 |

## Qualitative findings

- Four filaments (F1–F4) converge into a central hub region forming a hub-filament system.  
  > "Filamentary structures are identified using the 1.3 mm dust continuum map, with four of them converge into a dense central region, forming a hub-filament system (HFS)." (Abstract)
- Most protostellar cores show blue-asymmetric line profiles indicating infall, while several prestellar cores along filaments show red profiles indicating expansion or mass loss to the hub.  
  > "Investigation of H13CO+ and CCH spectral profiles revealed the majority of the cores having the characteristic blue asymmetric line profiles, typical signature of gravitational collapse. The remaining few cores showed red asymmetric profiles, indicative of gas expansion." (Abstract)
- Mass infall rates in hub protostellar cores are significantly higher than peripheral cores, supporting competitive accretion where the central gravitational potential funnels mass from less dominant cores.  
  > "Our results are supporting a competitive accretion scenario of massive star formation where gas is expected to be funnelled from less gravitationally dominant cores to the cores located at the gravitationally favorable position." (Abstract)

## Claim tuples

- H: Filaments in G318.049+00.086 channel mass into the central hub at rates sufficient to facilitate massive star formation. | E: Derived velocity gradients from PV diagrams along filament skeletons using H13CO+ (1-0) emission and computed mass inflow rates using a cylindrical inflow model with masses from LTE H13CO+ column density. | R: Measured velocity gradients of 10.9 to 22.1 km s-1 pc-1 and mass inflow rates of (1.3 to 5.0) x 10^3 Msun Myr-1 along filaments F1, F3, and F4. | F: The mass inflow rates (>10^3 Msun Myr-1) are sufficient to feed the central hub to form massive stars within ~2x10^4 years. | **supported**
- H: Dense cores in the protocluster exhibit localized collapse or expansion consistent with competitive accretion. | E: Fitted H13CO+ (1-0) and CCH (1-0) spectral profiles using the Hill5 radiative transfer model with MCMC sampling to derive infall velocities and mass infall rates. | R: Hub cores exhibit blue-asymmetric profiles with high infall rates (up to ~196 x 10^-5 Msun yr-1), whereas certain filament cores (cores 10, 11, 13) exhibit red-asymmetric profiles with expansion/mass-loss rates up to ~69 x 10^-5 Msun yr-1. | F: Gas is being funneled from less gravitationally dominant filament cores to cores in the central hub potential well, supporting competitive accretion. | **supported**

## Reasoning

- Why this data: ATOMS Band 3 line data trace large-scale kinematics and dense gas with low optical depth lines; ASSEMBLE Band 7 lines provide optically thin systemic velocities; QUARKS 1.3 mm continuum provides high angular resolution (~0.3″) to identify filament spines.  
  > "In this paper, we analyzed the filamentary structures traced by the 1.3 mm dust continuum and velocity distribution along their skeletons using H13CO+ (1–0), as well as infalling motions towards the embedded dense cores using H13CO+ (1–0) and CCH" (1.1 Selected region); "Furthermore, G318.049+00.086 was observed as part of the Querying Underlying mechanisms of massive star formation with ALMA-Resolved gas Kinematics and Structures (QUARKS) survey, complementing the ATOMS survey with an improved angular resolution (∼ 0.3″)." (2.3 QUARKS survey)
- Why this method: Hill5 model allows derivation of core infall velocities from asymmetric self-absorbed line profiles via radiative transfer in two approaching layers; FilFinder reliably extracts filament skeletons.  
  > "The infall velocity of the cores with blue profile was determined by fitting the observed spectral profiles of H13CO+ and CCH with the Hill5 infall model (cite: 2005ApJ...620..800D)." (3.5 Gas infall rates in cores); "The Hill5 model is a simple radiative transfer model used for deriving infall velocity in a contracting molecular cloud by dealing with radiative transfer processes in two approaching layers whose excitation temperatures linearly increase toward the inner region" (8 Hill5 Model Fit to the Infall Profiles)
- Alternative: Using HCO+ (1-0) or CS (2-1) for core infall was rejected because HCO+ is contaminated by outflows and CS has too coarse spectral resolution (~3 km/s).  
  > "In general, tracers like HCO+ (1–0) or CS (2–1) are best-served for this purpose. However, in our protocluster, the HCO+ line is significantly contaminated by outflow activities from the embedded protostars, while the CS line has a coarse spectral resolution of about 3 km s-1 that can significantly distort these characteristic features." (3.5 Gas infall rates in cores)
- Alternative: Cores 1, 2, 3, 4, 15, and 16 were excluded from filament analysis because 15 and 16 were outside the QUARKS FOV, core 1 is away from the main filament, and cores 2, 3, 4 trace extended filamentary material rather than compact cores.  
  > "Note that cores 15 and 16 are not present within the Field of View (FOV) of the 1.3 mm QUARKS data. Hence, we have not considered these cores in our subsequent analysis. Moreover, cores 1, 2, 3, and 4 are also excluded from further analysis." (1.1 Selected region)
- How they decided it was enough: Applied an S/N threshold >= 15 based on an rms noise of 0.27 K to select reliable spectra for Hill5 fitting.  
  > "To reliably determine the infall velocity from the asymmetric line profiles using the Hill5 model, we applied a signal-to-noise (S/N) threshold ≳ 15 to the observed spectra. The S/N ratio was calculated based on an rms noise level of 0.27 K" (3.5 Gas infall rates in cores)
- Limitation (authors): H13CO+ may not be strictly optically thin in dense cores, underestimating the column density by 27% to 93% if tau = 0.5-1.5.  
  > "The derived N(H2) value represents a lower limit to the true column density, as the assumption of the line to be optically thin is not always valid, specifically in the dense region" (3.2 Column density map); "If we consider H13CO+ has a moderate opacity (τ ∼ 0.5-1.5), the optically thin assumption would underestimate the column density by a factor τ /(1 - e-τ), corresponding to an increase of approximately ∼ 27%–93%" (3.2 Column density map)
- Limitation (authors): Assumed abundance [H13CO+/H2] of 10^-11 is uncertain across literature from 10^-10 to 10^-12, varying total mass estimates by up to a factor of 10.  
  > "While we adopted a representative value of [H13CO+/H2]=10-11, reported values span a wide range from 10-10 to 10-12. Adopting these extreme values would decrease or increase the inferred column density by an order of magnitude, respectively, implying that the total mass estimates could vary by up to a factor of 10." (3.2 Column density map)
- Limitation (authors): Unknown filament inclination introduces a factor of 2 uncertainty in mass inflow rates when inclination angle varies between 30 and 60 degrees.  
  > "We thus assume tan α = 1 in our calculation, and the estimated velocity gradients and mass inflow rates are expected to be uncertain by a factor of 2 when the α changes between 30◦ and 60◦ (cite: 2025A&A...704A..64W)." (3.4 Mass inflow rate along the filaments)
- Limitation (authors): Velocity gradient along filament F2 could not be determined due to large velocity fluctuations.  
  > "Note that we were unable to determine a consistent velocity gradient along the filament F2 due to significant velocity fluctuations along this filament." (3.3 Dynamical properties of filaments)
- Caveat (inferred, ours): Core expansion inferred from red-asymmetric profiles could potentially arise from complex foreground cloud motions or internal outflows rather than true expansion/stripping.
- Caveat (inferred, ours): Derivation of H2 column density directly from H13CO+ line intensity relies on a constant Tex equal to clump Tdust and a constant abundance ratio, which likely varies substantially between low-density envelopes and dense cores.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: FUNStools available at https://github.com/radioshiny/funstools; emcee available at https://github.com/dfm/emcee  
  > "https://github.com/radioshiny/funstools; https://github.com/dfm/emcee" (Footnotes 1 and 2)
- Missing: QUARKS project code is not printed in the paper text (only survey name cited).
- Missing: Specific tclean imaging scripts and exact channel selections used for continuum subtraction.
- Missing: Exact MCMC prior bounds and hyperparameter settings used in the second trial of Hill5 fitting.
- Data volume (inferred): 50 - 150 GB
- Score (inferred): 75/5, The paper provides clear quantitative details on the analysis pipeline (FilFinder, LTE column density equations, Hill5 MCMC modeling, cylindrical inflow calculations) and lists numerical results with uncertainties. However, it relies heavily on external core catalogs and reduced data products from prior ATOMS/ASSEMBLE/QUARKS papers, omits the QUARKS ALMA project ID, and does not provide tclean scripts or exact MCMC prior definitions.
- Rediscovery candidate: yes, All raw ALMA datasets (ATOMS 2019.1.00685.S, ASSEMBLE 2017.1.00545.S, and QUARKS archive data) are public in the ALMA archive. The mathematical formulae for column density, velocity gradient fitting, and mass inflow/infall rates are explicitly stated, allowing straightforward recalculation and reproduction of the main numerical findings.

## Links

- Method: 2015MNRAS.452.3435K (FilFinder algorithm for filament identification)
- Method: 2005ApJ...620..800D (Hill5 infall radiative transfer model)
- Method: 2013ascl.soft03002F (emcee MCMC implementation)
- Method: 2013ApJ...766..115K (Methodology for filament mass inflow rate calculation)
- Companion: 2020MNRAS.496.2790L (ATOMS survey overview and data reduction details)
- Companion: 2024RAA....24b5009L (QUARKS survey overview and continuum map preparation)
- Companion: 2024RAA....24f5011X (QUARKS Paper II detailing ACA observations and combination)
- Companion: 2024ApJS..270....9X (Identification and physical characterization of the 16 dense cores in G318.049+00.086)
- Companion: 2022MNRAS.514.6038Z (Previous ATOMS filament identification and velocity gradient study)
- Related: ATOMS
- Related: ASSEMBLE
- Related: QUARKS

## Checks

```json
{
 "quotes": 125,
 "quotes_ok": 105,
 "quote_pass_rate": 0.84,
 "quotes_too_long": 8,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 65,
  "rate": 0.707
 },
 "evidence_ok": false
}
```
