# Rotation curves in protoplanetary disks with thermal stratification. Physical model and observational evidence in MAPS disks

`2024A&A...686A...9M` | Astronomy and Astrophysics 2024 | first author: Martire, P. | arXiv: 2402.12236 | DOI: 10.1051/0004-6361/202348546

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Investigate the impact of vertical thermal stratification on the azimuthal velocity of protoplanetary disks and determine whether a stratified model can explain velocity differences between CO isotopologues.  
  > "We investigate the impact of thermal stratification on the azimuthal velocity of protoplanetary disks. High-resolution gas observations reveal velocity differences between CO isotopologues, which cannot be adequately explained with vertically isothermal models. The aim of this work is to determine whether a stratified model can explain this discrepancy." (abstract)
- Target **MWC 480**: coordinates _not stated_; z/distance d = 162pc  
  > "MWC 480 is a ∼ 7Myr Herbig Ae star located in the TaurusAurigae star-forming region at a distance of d = 162pc (Montesinos et al. 2009)." (4.3. MWC 480); distance from Montesinos et al. 2009  
  > "MWC 480 is a ∼ 7Myr Herbig Ae star located in the TaurusAurigae star-forming region at a distance of d = 162pc (Montesinos et al. 2009)." (4.3. MWC 480)
- Target **IM Lup**: coordinates _not stated_; z/distance 158pc  
  > "IM Lup is a young pre-main sequence star ( 1Myr) located in the Lupus star-forming region at a distance of 158pc (Gaia Collaboration et al. 2018)." (4.4. IM Lup); distance from Gaia Collaboration et al. 2018  
  > "IM Lup is a young pre-main sequence star ( 1Myr) located in the Lupus star-forming region at a distance of 158pc (Gaia Collaboration et al. 2018)." (4.4. IM Lup)
- Target **GM Aur**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 163296**: coordinates _not stated_; z/distance d = 101pc  
  > "HD 163296 is one of the most well-studied Herbig Ae star system at millimeter wavelengths thanks to its relative close distance ( d = 101pc) and bright disk." (4.6. HD 163296); distance from _not stated_
- Target **AS 209**: coordinates _not stated_; z/distance d ~ 121pc  
  > "AS 209 is a young T-Tauri star in the Ophiucus star forming region ( d ∼ 121pc)." (4.7. AS 209); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01055.L
- bands: _not stated_
- frequencies and spectral setup: 12CO and 13CO datacubes; continuum at 283 GHz  
  > "In particular, we used [12] CO and [13] CO datacubes." (abstract); "In addition, we computed the dust mass from millimetric emission at 283GHz, using (Hildebrand 1983):" (4.2. Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: MAPS ALMA Large Program (archival)  
  > "In this section, we describe how we applied the model to the entire sample of disks from the MAPS ALMA Large Program (Öberg et al. 2021)." (4.1. The curves)
- Line: 12CO not stated (not stated)
- Line: 13CO not stated (not stated)
- External data: Thermal parameters for the vertically isothermal model (H_100 and q)  
  > "For the vertically isothermal model, the thermal structure is defined by the hydrostatic height of the disk at R = 100au and the power law coefficient of the temperature profile, q . These parameters were taken from Zhang et al. (2021)." (4.1. The curves); "the thermal parameters for the isothermal model are taken from Zhang et al. (2021), for the stratified model from Law et al. (2021)." (Table 1) [from Zhang et al. (2021)]
- External data: 2D temperature structure parameters for the stratified model (T_mid, T_atm, q, q_atm, zeta_0, alpha, beta)  
  > "the thermal parameters for the isothermal model are taken from Zhang et al. (2021), for the stratified model from Law et al. (2021)." (Table 1 caption); "the thermal parameters for the isothermal model are taken from Zhang et al. (2021), for the stratified model from Law et al. (2021)." (Table 1) [from Law et al. (2021)]
- External data: Disk orientation parameters (i, PA) and 12CO and 13CO emitting surface parameters (z_0, psi, R_t, q_t)  
  > "where the best-fit parameters have been obtained by Izquierdo et al. (2023). All the parameters used are summarized in Table 1." (4.1. The curves); "The orientation parameters and the emitting surfaces are taken from Izquierdo et al. (2023)," (Table 1) [from Izquierdo et al. (2023)]
- Simulation/model as data: 3D SPH simulations of a thermally stratified protostellar disk using the phantom code with N = 10^6 gas particles based on MWC 480 parameters  
  > "In this work, we performed numerical smoothed particle hydrodynamics (SPH) simulations of protostellar disks using the phantom code (Price et al. 2018)." (3. Comparison with numerical simulations); "To test the analytical model, we simulated a thermally stratified disk using the parameters of MWC 480 presented in Law et al. (2021). The simulation has been performed with N = 10 [6] gas particles," (3. Comparison with numerical simulations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: MAPS datacubes and continuum fluxes used  
  > "In particular, we used [12] CO and [13] CO datacubes." (abstract); "In our analysis, we assumed T = 20K and ν = 283GHz, while the flux densities were extracted from MAPS data." (4.2. Results)
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
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Analytical derivation of density and velocity fields generalized from vertically isothermal disk models  
  > "In this paper, we analytically derive the density and velocity field of protostellar disks with thermal stratification, generalizing the work of Takeuchi & Lin (2002). A similar analysis of MAPS data with vertically isothermal disks was performed by Lodato et al. (2023)." (1. Introduction) [from Takeuchi & Lin (2002); Lodato et al. (2023)]
- 2D vertical temperature parameterization  
  > "In this work we will use the one by Dullemond et al. (2020), which is given by:" (2.3. Temperature prescriptions) [from Dullemond et al. (2020)]
- Double-Bell decomposition to distinguish between frontside and backside disk emission  
  > "Since three of the sources have strong contributions from the disk backside, we used a double-Bell decomposition to distinguish between these two components as introduced (Izquierdo et al. 2022)." (4.1. The curves) [from Izquierdo et al. (2022)]

### Not stated but needed to reproduce (our reading)

- Value of the surface density steepness parameter gamma used when fitting the MAPS observations (gamma = 1 is stated for the SPH simulation and implied in Eq. 26 for Toomre Q, but not explicitly stated for the observational rotation curve fits)
- Exact radial fitting ranges and radial binning used for the rotation curves of each disk
- MCMC sampler details (e.g., number of walkers, steps, burn-in, and prior distributions for M_star, M_d, and R_c)
- Distance assumed for GM Aur when computing dust mass from Eq. 25
- Exact method or aperture used to extract the 283 GHz continuum flux densities from MAPS data

## Analysis recipe

1. **Derive analytical model for density and azimuthal velocity in a thermally stratified disk**: Analytically solve vertical hydrostatic equilibrium and radial centrifugal balance including vertical temperature stratification and disk self-gravity, implemented in the code DYSC.  
  > "We analytically solved the hydrostatic equilibrium for a stratified disk and we derived the azimuthal velocity." (abstract); "Once the function f is defined, Eqs. (10) and (14) can be solved semi-analytically and entirely specify the rotation curve. We have implemented this calculation in DYSC [1] ." (2.3. Temperature prescriptions); "We simultaneously fitted the [12] CO and [13] CO data with both the isothermal and stratified model including the self gravitating contribution." (4.2. Results)
   - software: DYSC
   - assumption: Self-similar surface density profile from Lynden-Bell & Pringle (1974)  
  > "However, to apply the model to observations, we were forced to choose a parameterization for the surface density and we assume that it is described by the self-similar solution from Lynden-Bell & Pringle (1974):" (2.1. Assumptions)
   - assumption: Barotropic fluid in vertical hydrostatic equilibrium and radial centrifugal balance; mean molecular weight mu = 2.1  
  > "µ is the mean molecular weight (usually assumed to be 2.1)," (2.1. Assumptions); "Assuming a barotropic fluid, the pressure, P , is given by:" (2.1. Assumptions); "Assuming the condition of centrifugal balance, the rotation curve is given by the radial component of Navier-Stokes equation:" (2.2. Hydrostatic equilibrium and rotation curve)
   - assumption: Dullemond et al. (2020) 2D temperature prescription  
  > "In this work we will use the one by Dullemond et al. (2020), which is given by:" (2.3. Temperature prescriptions)
   - fitting: _not stated_
   - validation: Tested against 3D SPH numerical simulations and checked midplane temperature discrepancy in Appendix B  
  > "The stratified model perfectly describes the density and the velocity field of the simulation and is a significant improvement over the isothermal one." (3. Comparison with numerical simulations); "To examine this further, we conducted fits for these systems using both T mid ( R ) and T ( R , z = 0) as the midplane temperature. It was observed that this choice does not significantly alter the results." (Appendix B: Dullemond prescription)
2. **Validate analytical model with 3D SPH hydrodynamical simulations**: Run SPH simulation of a thermally stratified disk with MWC 480 parameters for eight outer orbits (~45 kyr) until relaxed, and compare azimuthally averaged density and velocity in 50 radial bins at z = 20 au (for R > 100 au) against isothermal and stratified analytical models.  
  > "To test the analytical model, we simulated a thermally stratified disk using the parameters of MWC 480 presented in Law et al. (2021)." (3. Comparison with numerical simulations); "We decided to analyze the output of the simulation after eight outer orbits (∼ 45kyr). In Fig. 1, we show a comparison between the density and the velocity of the simulations (red dots) at z = 20 au and both the isothermal and stratified model predictions." (3. Comparison with numerical simulations)
   - software: phantom
   - parameter: N = 10^6 gas particles, gamma = 1, R_c = 150 au, R_in = 10 au, R_out = 400 au, M_star = 2.1 M_sun, alpha_SS = 0.005  
  > "The simulation has been performed with N = 10 [6] gas particles, initially distributed as a tapered power law density profile, smoothed at the inner radius, with γ = 1 and R c = 150au, between R in = 10au and R out = 400au. The mass of the star is 2.1M ⊙ ." (3. Comparison with numerical simulations); "The α SS Shakura & Sunyaev (Shakura & Sunyaev 1973) viscosity coefficient has been set to 0.005." (3. Comparison with numerical simulations)
   - parameter: Dullemond temperature parameters: zeta_0 = 7 au, alpha = 2.78, beta = -0.05, T_mid,100 = 27 K, q = 0.23, T_atm,100 = 69 K, q_atm = 0.7  
  > "For the temperature structure we used the Dullemond prescription given by Eq. (19), with ζ 0 = 7au, α = 2.78, β = −0.05, T mid,100 = 27K, q = 0.23, T atm,100 = 69K, and q atm = 0.7." (3. Comparison with numerical simulations)
   - assumption: No self-gravity or dust included in the simulation  
  > "No self-gravity or dust have been included in the simulation." (3. Comparison with numerical simulations)
   - fitting: _not stated_
   - validation: System reaches relaxed hydrostatic equilibrium after a couple of orbits; inner points (R < 100 au) excluded due to vertical resolution issues at z = 20 au.  
  > "We observed that after a couple of orbits the system reaches a relaxed state." (3. Comparison with numerical simulations); "Since we are plotting quantities at z = 20 au, we have excluded the inner points because at those radii (R < 100 au) the disk has a smaller hydrostatic height H, causing numerical issues in the resolution of our simulation." (3. Comparison with numerical simulations)
3. **Extract 12CO and 13CO rotation curves from MAPS datacubes**: Extract frontside velocities from moment maps using Gaussian (MWC 480, AS 209) or double-Bell decomposition (IM Lup, GM Aur, HD 163296) based on velocity priors from discminer models.  
  > "Fig. 2. [12] CO and [13] CO rotation curves of the MAPS disks extracted with discminer." (Figure 2 caption); "Since three of the sources have strong contributions from the disk backside, we used a double-Bell decomposition to distinguish between these two components as introduced (Izquierdo et al. 2022). In this work, we have used an improved algorithm that performs this decomposition based on velocity priors obtained from the discminer models (Izquierdo et al. in prep)." (4.1. The curves)
   - software: discminer
   - parameter: Orientation (i, PA) and extraction methods (Gauss or Dbell) as listed in Table 1  
  > "Velocity extraction method, orientation parameters, thermal parameters and emitting surfaces for [12] CO and [13] CO data of the MAPS disks." (Table 1)
   - assumption: Emitting layer height parameterized as tapered power law z(R) with parameters from Izquierdo et al. (2023)  
  > "where z ( R ) is the height of the emitting layer of the considered molecule. For the emitting layer, we use:" (4.1. The curves); "where the best-fit parameters have been obtained by Izquierdo et al. (2023)." (4.1. The curves)
   - fitting: Gaussian or double-Bell line profile decomposition with discminer velocity priors  
  > "In this work, we have used an improved algorithm that performs this decomposition based on velocity priors obtained from the discminer models (Izquierdo et al. in prep)." (4.1. The curves)
   - validation: _not stated_
4. **Fit rotation curves for stellar mass, disk mass, and scale radius**: Simultaneously fit 12CO and 13CO rotation curves using MCMC for both vertically isothermal and thermally stratified models including disk self-gravity, and evaluate relative squared velocity differences (v_13^2 - v_12^2)/v_13^2.  
  > "We simultaneously fitted the [12] CO and [13] CO data with both the isothermal and stratified model including the self gravitating contribution." (4.2. Results); "We normalized the squared differences of the velocities by the square of the velocity for [13] CO since this quantity is independent of the stellar mass." (4.2. Results); "In Figs C.1 and C.2, we present the corner plots of the MCMC fitting procedure for the studied parameters under, respectively, the vertically isothermal and the stratified model." (Appendix C: Corner plots)
   - software: DYSC
   - parameter: Free parameters: M_star, M_d, R_c; fixed thermal and surface parameters from Table 1  
  > "we used it to fit for the star mass, disk mass, and scale radius of the sources in the MAPS sample." (abstract); "All the parameters used are summarized in Table 1." (4.1. The curves)
   - assumption: Fixed 1D/2D temperature profiles from Zhang et al. (2021) and Law et al. (2021) and fixed emitting surfaces from Izquierdo et al. (2023)  
  > "The orientation parameters and the emitting surfaces are taken from Izquierdo et al. (2023), the thermal parameters for the isothermal model are taken from Zhang et al. (2021), for the stratified model from Law et al. (2021)." (Table 1)
   - fitting: MCMC fitting procedure; goodness of fit evaluated via reduced chi-squared (chi^2_red)  
  > "Results of the fitting procedure and reduced chi-squared for the two different models: isothermal and stratified." (Table 2); "In Figs C.1 and C.2, we present the corner plots of the MCMC fitting procedure for the studied parameters under, respectively, the vertically isothermal and the stratified model." (Appendix C: Corner plots)
   - validation: Comparison of reduced chi-squared between isothermal and stratified models, and comparison of best-fit parameters with independent literature estimates.  
  > "It is evident from the results that the reduced χ [2] value consistently decreases when employing the stratified model." (5.1. Thermal stratification in MAPS disks)
5. **Compute dust masses, gas-to-dust ratios, and Toomre Q profiles**: Compute dust mass from 283 GHz continuum flux density using Hildebrand (1983) optically thin relation, combine with stratified-model disk gas mass to obtain gas-to-dust ratio, and compute radial Toomre Q profile using best-fit stratified parameters.  
  > "In addition, we computed the dust mass from millimetric emission at 283GHz, using (Hildebrand 1983):" (4.2. Results); "With the knowledge of the disk mass, it is possible to evaluate the gas-to-dust ratio, using Eq. (25) for the dust mass." (5.3. Gas-to-dust ratio); "To investigate the presence of gravitational instability, we used our best-fit parameters for the stratified model to compute the Toomre parameter (Toomre 1964)" (5.4. Toomre Q)
   - parameter: nu = 283 GHz, T = 20 K, kappa_nu = 2.3 (nu / 230 GHz)^0.4 cm^2 g^-1  
  > "where d is the distance, F ν is the flux density in Jy, κ ν = 2.3(ν/230GHz) [0][.][4] cm [2] g [−][1] is the dust opacity, and B ν is the blackbody spectrum. In our analysis, we assumed T = 20K and ν = 283GHz, while the flux densities were extracted from MAPS data." (4.2. Results)
   - assumption: Optically thin dust continuum emission at 283 GHz with T = 20 K; nearly Keplerian disk (kappa approx Omega) for Toomre Q; for AS 209, upper limit on M_d taken as 5% of M_star for gas-to-dust ratio.  
  > "We recall that this equation implies that dust emission is optically thin." (4.2. Results); "Indeed, according to Veronesi et al. (in prep), the minimum measurable mass with the rotation curve is 5% of the star mass. Taking this value as an upper limit for AS 209 disk mass, it is possible to give an upper limit for the gas-to-dust ratio." (5.3. Gas-to-dust ratio); "which, based on the hypothesis of nearly Keplerian disk (κ ≃ Ω), is" (5.4. Toomre Q)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DYSC** : Semi-analytical calculation and fitting of rotation curves in vertically isothermal and thermally stratified disks  
  > "Once the function f is defined, Eqs. (10) and (14) can be solved semi-analytically and entirely specify the rotation curve. We have implemented this calculation in DYSC [1] ." (2.3. Temperature prescriptions)
- **phantom** : 3D numerical smoothed particle hydrodynamics (SPH) simulations of a thermally stratified protostellar disk  
  > "In this work, we performed numerical smoothed particle hydrodynamics (SPH) simulations of protostellar disks using the phantom code (Price et al. 2018)." (3. Comparison with numerical simulations)
- **discminer** : Extracting 12CO and 13CO rotation curves and providing velocity priors for double-Bell decomposition  
  > "Fig. 2. [12] CO and [13] CO rotation curves of the MAPS disks extracted with discminer." (Figure 2 caption); "In this work, we have used an improved algorithm that performs this decomposition based on velocity priors obtained from the discminer models (Izquierdo et al. in prep)." (4.1. The curves)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MWC 480 stellar mass (isothermal model) | 1.969 | ±0.002 | M_⊙ | 4 | Isothermal 1.969 ±0.002 0.201±0.002 80±1 11.21 |
| MWC 480 disk mass (isothermal model) | 0.201 | ±0.002 | M_⊙ | 4 | Isothermal 1.969 ±0.002 0.201±0.002 80±1 11.21 |
| MWC 480 scale radius (isothermal model) | 80 | ±1 | au | 4 | Isothermal 1.969 ±0.002 0.201±0.002 80±1 11.21 |
| MWC 480 reduced chi-squared (isothermal model) | 11.21 | not stated | dimensionless | 4 | Isothermal 1.969 ±0.002 0.201±0.002 80±1 11.21 |
| MWC 480 stellar mass (stratified model) | 2.027 | ±0.002 | M_⊙ | 4 | Stratified 2.027±0.002 0.150 ± 0.002 128 ±1 6.14 |
| MWC 480 disk mass (stratified model) | 0.150 | ±0.002 | M_⊙ | 4 | Stratified 2.027±0.002 0.150 ± 0.002 128 ±1 6.14 |
| MWC 480 scale radius (stratified model) | 128 | ±1 | au | 4 | Stratified 2.027±0.002 0.150 ± 0.002 128 ±1 6.14 |
| MWC 480 reduced chi-squared (stratified model) | 6.14 | not stated | dimensionless | 4 | Stratified 2.027±0.002 0.150 ± 0.002 128 ±1 6.14 |
| IM Lup stellar mass (isothermal model) | 1.055 | ±0.002 | M_⊙ | 4 | Isothermal 1.055 ±0.002 0.200±0.003 55±1 35.68 |
| IM Lup disk mass (isothermal model) | 0.200 | ±0.003 | M_⊙ | 4 | Isothermal 1.055 ±0.002 0.200±0.003 55±1 35.68 |
| IM Lup scale radius (isothermal model) | 55 | ±1 | au | 4 | Isothermal 1.055 ±0.002 0.200±0.003 55±1 35.68 |
| IM Lup reduced chi-squared (isothermal model) | 35.68 | not stated | dimensionless | 4 | Isothermal 1.055 ±0.002 0.200±0.003 55±1 35.68 |
| IM Lup stellar mass (stratified model) | 1.194 | ±0.002 | M_⊙ | 4 | Stratified 1.194±0.002 0.106 ± 0.002 115 ±1 6.29 |
| IM Lup disk mass (stratified model) | 0.106 | ±0.002 | M_⊙ | 4 | Stratified 1.194±0.002 0.106 ± 0.002 115 ±1 6.29 |
| IM Lup scale radius (stratified model) | 115 | ±1 | au | 4 | Stratified 1.194±0.002 0.106 ± 0.002 115 ±1 6.29 |
| IM Lup reduced chi-squared (stratified model) | 6.29 | not stated | dimensionless | 4 | Stratified 1.194±0.002 0.106 ± 0.002 115 ±1 6.29 |
| GM Aur stellar mass (isothermal model) | 0.872 | ±0.003 | M_⊙ | 4 | Isothermal 0.872 ±0.003 0.312±0.003 56±1 90.84 |
| GM Aur disk mass (isothermal model) | 0.312 | ±0.003 | M_⊙ | 4 | Isothermal 0.872 ±0.003 0.312±0.003 56±1 90.84 |
| GM Aur scale radius (isothermal model) | 56 | ±1 | au | 4 | Isothermal 0.872 ±0.003 0.312±0.003 56±1 90.84 |
| GM Aur reduced chi-squared (isothermal model) | 90.84 | not stated | dimensionless | 4 | Isothermal 0.872 ±0.003 0.312±0.003 56±1 90.84 |
| GM Aur stellar mass (stratified model) | 1.128 | ±0.002 | M_⊙ | 4 | Stratified 1.128±0.002 0.118±0.002 96 ±1 8.48 |
| GM Aur disk mass (stratified model) | 0.118 | ±0.002 | M_⊙ | 4 | Stratified 1.128±0.002 0.118±0.002 96 ±1 8.48 |
| GM Aur scale radius (stratified model) | 96 | ±1 | au | 4 | Stratified 1.128±0.002 0.118±0.002 96 ±1 8.48 |
| GM Aur reduced chi-squared (stratified model) | 8.48 | not stated | dimensionless | 4 | Stratified 1.128±0.002 0.118±0.002 96 ±1 8.48 |
| HD 163296 stellar mass (isothermal model) | 1.842 | ±0.002 | M_⊙ | 4 | Isothermal 1.842 ±0.002 0.124±0.001 38±1 29.60 |
| HD 163296 disk mass (isothermal model) | 0.124 | ±0.001 | M_⊙ | 4 | Isothermal 1.842 ±0.002 0.124±0.001 38±1 29.60 |
| HD 163296 scale radius (isothermal model) | 38 | ±1 | au | 4 | Isothermal 1.842 ±0.002 0.124±0.001 38±1 29.60 |
| HD 163296 reduced chi-squared (isothermal model) | 29.60 | not stated | dimensionless | 4 | Isothermal 1.842 ±0.002 0.124±0.001 38±1 29.60 |
| HD 163296 stellar mass (stratified model) | 1.948 | ±0.002 | M_⊙ | 4 | Stratified 1.948±0.002 0.134 ± 0.001 91 ±1 19.74 |
| HD 163296 disk mass (stratified model) | 0.134 | ±0.001 | M_⊙ | 4 | Stratified 1.948±0.002 0.134 ± 0.001 91 ±1 19.74 |
| HD 163296 scale radius (stratified model) | 91 | ±1 | au | 4 | Stratified 1.948±0.002 0.134 ± 0.001 91 ±1 19.74 |
| HD 163296 reduced chi-squared (stratified model) | 19.74 | not stated | dimensionless | 4 | Stratified 1.948±0.002 0.134 ± 0.001 91 ±1 19.74 |
| AS 209 stellar mass (isothermal model) | 1.272 | ±0.003 | M_⊙ | 4 | Isothermal 1.272 ±0.003 0.042±0.003 45±1 25.13 |
| AS 209 disk mass (isothermal model) | 0.042 | ±0.003 | M_⊙ | 4 | Isothermal 1.272 ±0.003 0.042±0.003 45±1 25.13 |
| AS 209 scale radius (isothermal model) | 45 | ±1 | au | 4 | Isothermal 1.272 ±0.003 0.042±0.003 45±1 25.13 |
| AS 209 reduced chi-squared (isothermal model) | 25.13 | not stated | dimensionless | 4 | Isothermal 1.272 ±0.003 0.042±0.003 45±1 25.13 |
| AS 209 stellar mass (stratified model) | 1.311 | ±0.001 | M_⊙ | 4 | Stratified 1.311±0.001 0.0002 ± 0.0002 126 ±2 10.55 |
| AS 209 disk mass (stratified model) | 0.0002 | ±0.0002 | M_⊙ | 4 | Stratified 1.311±0.001 0.0002 ± 0.0002 126 ±2 10.55 |
| AS 209 scale radius (stratified model) | 126 | ±2 | au | 4 | Stratified 1.311±0.001 0.0002 ± 0.0002 126 ±2 10.55 |
| AS 209 reduced chi-squared (stratified model) | 10.55 | not stated | dimensionless | 4 | Stratified 1.311±0.001 0.0002 ± 0.0002 126 ±2 10.55 |
| MWC 480 continuum flux at 283 GHz | 943.51 | not stated | mJy | 5 | MWC 480 943.51 0.00138 108 |
| MWC 480 dust mass | 0.00138 | not stated | M_⊙ | 5 | MWC 480 943.51 0.00138 108 |
| MWC 480 gas-to-dust ratio | 108 | not stated | dimensionless | 5 | MWC 480 943.51 0.00138 108 |
| IM Lup continuum flux at 283 GHz | 536.25 | not stated | mJy | 5 | IM Lup 536.25 0.00075 134 |
| IM Lup dust mass | 0.00075 | not stated | M_⊙ | 5 | IM Lup 536.25 0.00075 134 |
| IM Lup gas-to-dust ratio | 134 | not stated | dimensionless | 5 | IM Lup 536.25 0.00075 134 |
| GM Aur continuum flux at 283 GHz | 347.95 | not stated | mJy | 5 | GM Aur 347.95 0.00049 240 |
| GM Aur dust mass | 0.00049 | not stated | M_⊙ | 5 | GM Aur 347.95 0.00049 240 |
| GM Aur gas-to-dust ratio | 240 | not stated | dimensionless | 5 | GM Aur 347.95 0.00049 240 |
| HD 163296 continuum flux at 283 GHz | 1127.97 | not stated | mJy | 5 | HD 163296 1127.97 0.00064 202 |
| HD 163296 dust mass | 0.00064 | not stated | M_⊙ | 5 | HD 163296 1127.97 0.00064 202 |
| HD 163296 gas-to-dust ratio | 202 | not stated | dimensionless | 5 | HD 163296 1127.97 0.00064 202 |
| AS 209 continuum flux at 283 GHz | 414.83 | not stated | mJy | 5 | AS 209 414.83 0.00034 < 192 |
| AS 209 dust mass | 0.00034 | not stated | M_⊙ | 5 | AS 209 414.83 0.00034 < 192 |
| AS 209 gas-to-dust ratio | < 192 | not stated | dimensionless | 5 | AS 209 414.83 0.00034 < 192 |
| GM Aur minimum Toomre Q | 4 | not stated | dimensionless | 5 | Interestingly, the two disks that showed spiral structures (IM Lup and GM Aur) have a Toomre profile that is lower than the others, with a minimum value of ∼ 4 for GM Aur and ∼ 6 for IM Lup. |
| IM Lup minimum Toomre Q | 6 | not stated | dimensionless | 5 | Interestingly, the two disks that showed spiral structures (IM Lup and GM Aur) have a Toomre profile that is lower than the others, with a minimum value of ∼ 4 for GM Aur and ∼ 6 for IM Lup. |

## Qualitative findings

- A vertically isothermal model can only produce a relative squared velocity shift between 12CO and 13CO of less than 5%; larger shifts indicate significant vertical thermal stratification.  
  > "Hence, if the quantity ( v [2] 13 [−] [v] 12 [2] [)/] [v] [2] k [is] [higher] [than] [5%,] [the] [system] [cannot] [be] [de-] scribed by an isothermal model, while it is likely that vertical stratification plays a significant role." (4.2. Results)
- Including thermal stratification consistently reduces the reduced chi-squared and yields more realistic stellar masses, disk masses, and scale radii across the MAPS sample compared to vertically isothermal models.  
  > "The best-fit values of star mass, disk mass, and scale radius become more realistic and more in line with previous studies. In particular, the quality of the scale radius estimate significantly increases when adopting a stratified model." (abstract); "It is evident from the results that the reduced χ [2] value consistently decreases when employing the stratified model." (5.1. Thermal stratification in MAPS disks)
- All studied MAPS disks are gravitationally stable according to the Toomre criterion (Q > 1), though disks with spiral structures (IM Lup and GM Aur) have lower minimum Q values (~4-6).  
  > "The Toomre Q parameter suggests that the disks are gravitationally stable ( Q - 1). However, the systems that show spirals presence are closer to the conditions of gravitational instability ( Q ∼ 5)." (abstract); "Interestingly, the two disks that showed spiral structures (IM Lup and GM Aur) have a Toomre profile that is lower than the others, with a minimum value of ∼ 4 for GM Aur and ∼ 6 for IM Lup." (5.4. Toomre Q)

## Claim tuples

- H: A vertically thermally stratified hydrostatic disk model accurately describes the density and azimuthal velocity fields of a stratified protoplanetary disk. | E: Derive the analytical density and rotation curve equations for a thermally stratified disk and compare them against 3D SPH simulations of a stratified disk (MWC 480 setup) using phantom. | R: At z = 20 au after eight outer orbits, the sub-Keplerian deviation (v_k^2 - v_phi^2)/v_k^2 reaches 10-12% and is matched by the stratified model, whereas the isothermal model fails to reproduce the density and velocity profiles. | F: The analytical thermally stratified model accurately describes the simulated density and velocity fields and is a major improvement over the vertically isothermal model. | **supported**
- H: Vertical thermal stratification can explain the observed velocity differences between 12CO and 13CO rotation curves in MAPS protoplanetary disks and improve dynamical estimates of star mass, disk mass, and scale radius. | E: Simultaneously fit 12CO and 13CO rotation curves of the five MAPS disks using both vertically isothermal and thermally stratified self-gravitating models. | R: The reduced chi-squared decreases for all five disks when using the stratified model (e.g., from 90.84 to 8.48 in GM Aur and from 35.68 to 6.29 in IM Lup), and best-fit scale radii increase from 38-80 au to more realistic values of 91-128 au. | F: Thermal stratification reconciles most of the velocity inconsistencies between 12CO and 13CO and provides more realistic stellar masses, disk masses, and scale radii, though localized deviations remain in the outer disk of IM Lup, substructured regions of HD 163296, and the compact inner disk of AS 209. | **supported**
- H: Dynamical disk masses derived from thermally stratified rotation curve models yield standard gas-to-dust ratios and indicate whether the MAPS disks are gravitationally unstable. | E: Combine the stratified-model disk gas masses with optically thin 283 GHz dust masses to compute gas-to-dust ratios, and evaluate radial Toomre Q profiles. | R: Inferred gas-to-dust ratios range between 108 and 240 (< 192 for AS 209), and Toomre Q is greater than 1 everywhere, with minimum values of ~4 in GM Aur and ~6 in IM Lup. | F: The gas-to-dust ratios are within a factor of ~2 of the standard value of 100, and all disks are gravitationally stable according to Q > 1, though spiral-hosting disks (GM Aur and IM Lup) are closer to the instability regime. | **supported**

## Reasoning

- Why this data: The MAPS ALMA Large Program provides high spatial and spectral resolution 12CO and 13CO observations with established 2D thermal structures and emitting surfaces for five protoplanetary disks.  
  > "More recently, the large program Molecules with ALMA at Planet-forming Scales (MAPS) (Öberg et al. 2021) targeted five protoplanetary disks (MWC 480, IM Lup, GM Aur, HD 163296, and AS 209) in several molecular lines." (1. Introduction); "temperature structure of the MAPS disks, using the Dullemond et al. (2020) prescription given by Eq. (19)." (4.1 The curves)
- Why this method: Analytical hydrostatic and centrifugal balance modeling generalized to include 2D temperature gradients captures both radial and vertical temperature gradients affecting azimuthal velocity; double-Bell decomposition isolates frontside emission when backside contamination is strong.  
  > "Since three of the sources have strong contributions from the disk backside, we used a double-Bell decomposition to distinguish between these two components as introduced (Izquierdo et al. 2022)." (4.1. The curves); "However, as shown in Appendix A, in the azimuthal velocity, it is not only essential to know the temperature at ( R , z ), but also its radial and vertical gradient at that location." (4.5. GM Aur)
- Alternative: Vertically isothermal disk model (tested and rejected in favor of the thermally stratified model due to poorer fits and unrealistic scale radii)  
  > "It is evident from the results that the reduced χ [2] value consistently decreases when employing the stratified model. This indicates that the inclusion of thermal stratification provides a more effective way of describing the observed data." (5.1. Thermal stratification in MAPS disks)
- Alternative: Dartois et al. (2003) vertical temperature parameterization (mentioned as an alternative to Dullemond et al. 2020)  
  > "The two parameterizations of the vertical temperature more often used are given by Dartois et al. (2003) and Dullemond et al. (2020). In this work we will use the one by Dullemond et al. (2020), which is given by:" (2.3. Temperature prescriptions)
- Alternative: Using T(R, z=0) instead of T_mid(R) as the midplane temperature in the Dullemond et al. (2020) prescription (tested in Appendix B, found not to significantly alter results)  
  > "To examine this further, we conducted fits for these systems using both T mid ( R ) and T ( R , z = 0) as the midplane temperature. It was observed that this choice does not significantly alter the results." (Appendix B: Dullemond prescription)
- How they decided it was enough: _not stated_
- Limitation (authors): In the Dullemond et al. (2020) temperature prescription, f(R, z=0) != 1 so the temperature does not smoothly connect to T_mid at the midplane (up to ~5% discrepancy at 100 au).  
  > "and the temperature does not smoothly connect to its value at midplane" (Appendix B)
- Limitation (authors): In the outer disk of IM Lup, diffuse emission (possibly due to external photoevaporation) affects emitting surface retrieval and velocity extraction, and neither model explains the large velocity difference there.  
  > "At R ∼ 250au, the difference in the data between 12 CO and 13 CO is on the order of ∼ 10% and it significantly increases in the outer part. There, neither the stratified model is able to explain that difference." (4.4. IM Lup); "Izquierdo et al. (2023) pointed out that the emission from the outer disk is so diffuse that the retrieval of the emitting surface, as well as the velocity extraction, needs to be taken with care." (4.4. IM Lup)
- Limitation (authors): In HD 163296, pressure-modulated substructures in the rotation curves are not included in the smooth self-similar surface density model, impacting fit quality.  
  > "The presence of pressure modulated substructures in the rotation curves (Izquierdo et al. 2023) impacts the quality of the fit (clearly visible in Fig. 3). One possible solution would be to include them in the fitting model." (4.6. HD 163296)
- Limitation (authors): In AS 209, disk compactness and beam smearing affect emitting surface and velocity extraction in the inner disk (< 125 au), causing 13CO to appear slower than 12CO.  
  > "Interestingly, when inspecting the rotation curves of AS 209 (Fig. 2), the [13] CO is slower compared to the [12] CO, despite it being closer to the midplane. This trend is observed up to ∼ 125au. A possible explanation for this is the compactness of the disk, which makes more difficult to extract a precise emitting surface due to beam smearing." (4.7. AS 209)
- Limitation (authors): Dust mass calculation assumes optically thin dust emission and fixed opacity, which can underestimate dust mass by more than a factor of 2 and vary by a factor of ~10 with grain properties.  
  > "Indeed, as we have already mentioned, the optically thin hypothesis for dust emission could lead to a difference of a more than a factor of 2 in the dust mass calculation (Guidi et al. 2016), underestimating it. In addition, the dust opacity could also vary of a factor of ∼ 10, depending on the grain size and composition." (5.3. Gas-to-dust ratio)
- Limitation (authors): Minimum measurable disk mass from rotation curves is ~5% of the stellar mass, so the low disk mass of AS 209 is compatible with zero.  
  > "while for the disk mass we report a 3−σ upper limit of M d = 0.00025±0.00025M ⊙ , since the best-fit parameter is compatible with zero." (4.7. AS 209); "Indeed, according to Veronesi et al. (in prep), the minimum measurable mass with the rotation curve is 5% of the star mass." (5.3. Gas-to-dust ratio)
- Caveat (inferred, ours): Formal MCMC uncertainties on M_star (~0.001-0.002 M_sun), M_d (~0.001-0.002 M_sun), and R_c (~1 au) are purely statistical and neglect systematic uncertainties in disk inclination, distance, emitting surface heights z(R), and the fixed 2D temperature parameters.
- Caveat (inferred, ours): Reduced chi-squared values remain significantly greater than 1 (6.14 to 19.74) even for the stratified model, indicating unmodeled physical substructures or underestimated velocity uncertainties.
- Caveat (inferred, ours): The rotation curves for IM Lup and GM Aur were re-extracted using an unpublished algorithm (Izquierdo et al. in prep) and differ from those used in Lodato et al. (2023).

## Reproducibility

- Data public (paper): Uses ALMA data from ADS/JAO.ALMA#2018.1.01055.L (MAPS Large Program)  
  > "In this section, we describe how we applied the model to the entire sample of disks from the MAPS ALMA Large Program (Öberg et al. 2021)." (4.1. The curves); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01055.L." (Acknowledgements)
- Products in archive: _not stated_
- Code: DYSC code is publicly available at https://github.com/crislong/DySc  
  > "Once the function f is defined, Eqs. (10) and (14) can be solved semi-analytically and entirely specify the rotation curve. We have implemented this calculation in DYSC [1] ." (2.3. Temperature prescriptions); "1 The code is publicly available at https://github.com/crislong/DySc" (Footnote 1)
- Missing: Exact version/implementation of the improved double-Bell decomposition algorithm with discminer velocity priors (cited as Izquierdo et al. in prep) used to extract the rotation curves in Fig. 2
- Missing: Exact radial fitting ranges and data filtering applied to the 12CO and 13CO rotation curves during the MCMC fits
- Missing: Explicit value of gamma used in the observational fits (assumed to be 1) and MCMC prior bounds
- Missing: Assumed distance for GM Aur in the dust mass calculation
- Data volume (inferred): A few GB for the high-resolution MAPS 12CO and 13CO image cubes and 283 GHz continuum maps of the 5 targets (or <10 MB if starting from extracted 1D rotation curves).
- Score (inferred): 78/5, The analytical model is fully derived in the paper, the fitting code (DYSC) is publicly released on GitHub, all input thermal/surface/orientation parameters are tabulated in Table 1, and the MAPS data are public; however, the exact rotation curve extraction relies on an improved double-Bell algorithm cited as 'Izquierdo et al. in prep' and exact radial fitting ranges are not specified.
- Rediscovery candidate: yes, Public MAPS ALMA datacubes, publicly released modeling code (DYSC), complete input parameter tables (Table 1), and clear numeric answer keys (Tables 2 and 3) make this an excellent candidate for reproducing dynamical mass and scale radius fits.

## Links

- Method: Takeuchi & Lin (2002) (Foundational analytical derivation of density and velocity fields in vertically isothermal disks that this paper generalizes)
- Method: Lodato et al. (2023) (Vertically isothermal self-gravitating rotation curve analysis of MAPS disks that serves as the baseline methodology)
- Method: Dullemond et al. (2020) (2D vertical temperature stratification parameterization used in the analytical model)
- Method: Price et al. (2018) (Reference for the phantom SPH code used for numerical validation)
- Method: Izquierdo et al. (2021, 2022, 2023) (discminer framework and double-Bell decomposition method used to extract rotation curves and emitting surfaces)
- Companion: Öberg et al. (2021) (MAPS ALMA Large Program overview paper)
- Companion: Law et al. (2021) (MAPS paper providing the 2D temperature structure parameters)
- Companion: Zhang et al. (2021) (MAPS paper providing the isothermal scale height and temperature parameters)
- Companion: Izquierdo et al. (2023) (Paper providing the discminer orientation and emitting surface parameters for the MAPS sample)
- Related: MAPS (Molecules with ALMA at Planet-forming Scales)

## Checks

```json
{
 "quotes": 161,
 "quotes_ok": 161,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 18,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 57,
 "numeric_problems": 0,
 "fill": {
  "facts": 105,
  "stated": 58,
  "rate": 0.552
 },
 "evidence_ok": true
}
```
