# Modeling the Mass Distribution and Gravitational Potential of Nearby Disk Galaxies: Implications for the Interstellar Medium Dynamical Equilibrium

`2025ApJ...989...66V` | The Astrophysical Journal 2025 | first author: Vijayakumar, Vivek | arXiv: 2506.22381 | DOI: 10.3847/1538-4357/ade800

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: Model stellar, gas and dark matter mass distributions of 17 nearby massive disk galaxies, and from them the gravitational potential, gas vertical scale height and ISM weight (vertical dynamical equilibrium)  
  > "This work aims at modeling the stellar, gas, and dark matter distribution for a sample of nearby, massive, star-forming disk galaxies." (Introduction)
- Target **17 massive star-forming PHANGS-ALMA disk galaxies (NGC 1087, 1300, 1385, 1512, 2283, 2835, 2903, 2997, 3137, 3507, 3511, 3521, 3621, 4303, 4571, 4781, 5042)**: coordinates _not stated_; z/distance 7.1 to 23.6 Mpc (Table 1, per galaxy)  
  > "(2) galaxy distance (cite: Anand_etal_2021)" (Table 1 notes); "(4-5) inclination and position angles (cite: rotation)" (Table 1 notes); distance from Anand et al. 2021 (cite: Anand_etal_2021)  
  > "(2) galaxy distance (cite: Anand_etal_2021)" (Table 1 notes); "(4-5) inclination and position angles (cite: rotation)" (Table 1 notes)

## Data provenance

- ALMA projects: 2015.1.00925.S, 2015.1.00956.S, 2017.1.00392.S, 2017.1.00886.L, 2018.1.01651.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: CO(2-1) data from the PHANGS-ALMA survey, used via derived radial profiles and rotation curves  
  > "obtained as part of the PHANGS-ALMA survey (cite: Leroy2021)" (2.3 CO Data Tracing Molecular Gas Distribution)
- Line: CO 2-1 (not stated)
- Other facility **Spitzer IRAC 3.6 micron (S4G and Querejeta et al. 2021 processed images)**: Near-IR surface brightness tracing stellar mass  
  > "Our analysis leverages near-IR imaging data taken by the IRAC instrument on the" (2.1 Near-IR Data Tracing Stellar Distribution)
- Other facility **VLA (THINGS and PHANGS-VLA)**: H I 21 cm line data for atomic gas surface density, rotation curves and velocity dispersion  
  > "We make use of H I 21 cm line observations taken by the Very Large Array (VLA), as part of the THINGS (cite: Walter2008) and PHANGS–VLA surveys (cite: Chiang_etal_2024)." (2.2 H I Data Tracing Atomic Gas Distribution)
- External data: Radial profiles of molecular gas, atomic gas and stellar mass surface density (and the CO and H I intensity profiles behind them)  
  > "These data have been compiled and converted into radial profiles of molecular gas, atomic gas, and stellar mass surface densities by (cite: Sun2022)." (Data) [from Sun et al. 2022 (cite: Sun2022)]
- External data: Radial bin width of the 3.6 micron surface brightness profiles: 500 pc  
  > "(with a fixed radial bin width of 500 pc)" (2.1 Near-IR Data Tracing Stellar Distribution) [from Sun et al. 2022 (cite: Sun2022)]
- External data: CO rotation curves, assuming fixed position and inclination angles  
  > "The CO rotation curves were measured by (cite: rotation), assuming fixed position and inclination angles across each galaxy disk." (2.4 CO and H I Kinematic Measurements) [from Lang et al. 2020 (cite: rotation)]
- External data: H I rotation curves for the THINGS galaxies (derived with 3D-Barolo)  
  > "we use the rotation curves derived by (cite: DiTeodoro_Peek_2021) with 3D-Barolo" (2.4 CO and H I Kinematic Measurements) [from Di Teodoro & Peek 2021 (cite: DiTeodoro_Peek_2021)]
- External data: Empirical, spatially varying stellar mass-to-light ratio at 3.6 micron  
  > "The same galaxies also have empirical stellar M/L ratio estimates from (cite: Leroy2019)" (Introduction) [from Leroy et al. 2019; Leroy et al. 2021 (cite: Leroy2019; Leroy2021)]
- External data: Galaxy distances  
  > "(2) galaxy distance (cite: Anand_etal_2021)" (Table 1 notes) [from Anand et al. 2021 (cite: Anand_etal_2021)]
- External data: Global stellar masses  
  > "(3) global stellar mass (cite: Leroy2021)" (Table 1 notes) [from Leroy et al. 2021 (cite: Leroy2021)]
- External data: Inclination and position angles  
  > "(4-5) inclination and position angles (cite: rotation)" (Table 1 notes) [from Lang et al. 2020 (cite: rotation)]
- External data: CO velocity dispersion measured at fixed 150 pc scales  
  > "The CO velocity dispersion is measured at fixed 150 pc scales (cite: Sun2018; Sun2020a)" (2.4 CO and H I Kinematic Measurements) [from Sun et al. 2018; Sun et al. 2020b (cite: Sun2018; Sun2020a)]
- External data: SFR surface density measurements  
  > "we use existing SFR surface density measurements for the these galaxies by (cite: Sun_etal_2023)" (4.4 Gas Weight and Star Formation) [from Sun et al. 2023 (cite: Sun_etal_2023)]
- External data: Stellar bar information used to select galaxies  
  > "For galaxies hosting stellar bars (cite: Querejeta_etal_2021)" (Data) [from Querejeta et al. 2021 (cite: Querejeta_etal_2021)]
- Simulation/model as data: TIGRESS-based power-law prediction of the SFR surface density versus weight relation (Ostriker & Kim 2022) used as comparison  
  > "predicts the following power-law relation based on the TIGRESS simulations" (4.4 Gas Weight and Star Formation)

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

- Full descriptions of the key observational measurements (profiles, rotation curves) are deferred to the original references  
  > "refer the reader to the original references for full descriptions." (Data) [from Sun2022; Leroy2021; Lang et al. 2020 (cite: rotation)]
- CO-to-H2 conversion factor alpha_CO(2-1) derived following best practices  
  > "derived following current best practices suggested by (cite: Schinnerer_Leroy_2024)" (2.3 CO Data Tracing Molecular Gas Distribution) [from (cite: Schinnerer_Leroy_2024)]
- 3D-Barolo modeling procedure for PHANGS-VLA H I cubes  
  > "For further technical details on the modeling procedure, we refer to (cite: DiTeodoro+2023)." (2.4 CO and H I Kinematic Measurements) [from (cite: DiTeodoro+2023)]
- Stellar disk midplane potential for an exponential vertical distribution  
  > "we follow (cite: Bovy) to derive the potential near the galaxy midplane" (3.1 Stellar and Gas Disk Potentials) [from (cite: Bovy)]
- Thin gas disk potential via complete elliptic integral  
  > "we assume a geometrically thin disk and follow (cite: 2008gady.book.....B) to derive the potential" (3.1 Stellar and Gas Disk Potentials) [from (cite: 2008gady.book.....B)]
- Maximum disk normalisation (total baryons = 0.85 of dynamical mass at 2.2 scale lengths)  
  > "The choice to normalize the total baryonic contribution to 0.85 times the dynamical mass implied by the circular velocity is empirically determined in previous studies (cite: maximaldisk)." (3.2 Rescaling of the H I Rotation Curves and the Stellar Potential) [from (cite: maximaldisk)]
- Fixed fiducial NFW scale radius R_s = 9 H_star for the one-parameter fit  
  > "a one-parameter model with a fixed fiducial $R_s = 9H_\star$ (cite: Somerville2025)" (3.3 Rotation Curve Fitting) [from (cite: Somerville2025)]
- Cubic equation for the equilibrium gas scale height  
  > "In practice, this requires solving a cubic equation (cite: Hassan_etal_2024)" (3.4 Disk Scale Height) [from (cite: Hassan_etal_2024)]
- Effective gas velocity dispersion as the mass-weighted average of molecular and atomic dispersions  
  > "we use the mass-weighted average of the molecular and atomic gas velocity dispersion" (3.4 Disk Scale Height) [from (cite: Sun2020)]
- Fiducial H_star = 0.27 l_star  
  > "The conventional estimate of $H_\star = 0.27\,\ell_\star$" (3.4 Disk Scale Height) [from (cite: Kregel2002; Sun2020)]
- Rescaled H_star = 0.09 l_star based on Milky Way scale length and scale height  
  > "A rescaled version of the above, $H_\star = 0.09\,\ell_\star$" (3.4 Disk Scale Height) [from (cite: Bovy_Rix_2013; Zhang2013)]

### Not stated but needed to reproduce (our reading)

- Exact ALMA and VLA datasets, product versions and cube/moment choices behind the Sun et al. 2022 profiles (only PHANGS-ALMA and PHANGS-VLA/THINGS are named)
- The per-galaxy numerical profiles (Sigma_star, Sigma_atom, Sigma_mol, sigma_eff, rotation curves) are not tabulated; a reproducer must obtain them from Sun et al. 2022 / MegaTable and Lang et al. 2020
- Gaussian process kernel amplitude, noise term and optimiser settings (only RBF kernel and length scales of 3 kpc and 1.5 kpc given)
- Radius ranges excluded for bars and central structures, and the outlier-rejection settings used to fit l_star
- The optimiser, weights (beyond the larger H I point weights), uncertainties and priors used for the NFW fit, and how BIC was computed
- 3D-Barolo run parameters for the PHANGS-VLA cubes (masks, ring widths, initial guesses)
- How the H_star = H_gas case was solved numerically across radius
- The radial extent and fitting range used for the exponential extrapolation of surface density profiles
- Which version of the alpha_CO prescription and CO excitation ratio was used

## Analysis recipe

1. **Derive H I rotation curves for galaxies without THINGS curves**: 3D-Barolo tilted-ring modeling of PHANGS-VLA H I cubes in two steps: geometry, then rotation velocity and velocity dispersion  
  > "Our modeling followed a standard two-step approach, with the first step devoted to determining the galaxy geometry" (2.4 CO and H I Kinematic Measurements)
   - software: 3D-Barolo
   - parameter: 3D-Barolo version 1.7  
  > "we perform similar kinematic modeling with 3D-Barolo (version 1.7) on the PHANGS–VLA H I data cubes" (2.4 CO and H I Kinematic Measurements)
   - parameter: Inclination and position angles vary with galactocentric radius  
  > "The inclination and position angles are allowed to vary as a function of galactocentric radius" (2.4 CO and H I Kinematic Measurements)
   - fitting: _not stated_
   - validation: H I rotation curves for THINGS galaxies verified as consistent with literature curves from the same data  
  > "We have verified that these rotation curves are quantitatively consistent with those derived and presented by (cite: things) and (cite: Frank2016) based on the same THINGS data." (2.4 CO and H I Kinematic Measurements)
2. **Smooth and extend the surface density profiles**: Gaussian process regression with a radial basis function kernel; exponential fits to outer parts extrapolated to match H I rotation curve coverage  
  > "we perform a Gaussian process regression to damp out small-scale fluctuations in the surface density profiles" (3.1 Stellar and Gas Disk Potentials); "we fit exponential models to their outer parts and extrapolate them to match the corresponding H I rotation curve coverage" (3.1 Stellar and Gas Disk Potentials)
   - parameter: Length scales 3 kpc (stellar) and 1.5 kpc (gas)  
  > "the optimal length scales for the stellar and gas profiles are 3 kpc and 1.5 kpc, respectively" (3.1 Stellar and Gas Disk Potentials)
   - assumption: Outer stellar profiles are well described by exponentials  
  > "Considering that these galaxies are well described by exponential profiles near the outskirts" (3.1 Stellar and Gas Disk Potentials)
   - fitting: _not stated_
   - validation: Length scales tested and outcomes inspected visually  
  > "We test different length scales on our data and visually inspect the outcomes" (3.1 Stellar and Gas Disk Potentials)
3. **Compute stellar and gas potentials and circular velocities**: Numerically integrate the exponential-thick stellar disk potential and the thin gas disk potential, then V^2 = R dPhi/dR  
  > "We derive the potentials for each component, $\Phi_\star(R)$ and $\Phi_\mathrm{gas}(R)$, by numerically integrating" (3.1 Stellar and Gas Disk Potentials)
   - assumption: Stellar disk: exponential vertical distribution with constant H_star; gas disk: geometrically thin  
  > "assuming an exponential vertical distribution with a constant vertical scale height" (3.1 Stellar and Gas Disk Potentials); "we assume a geometrically thin disk" (3.1 Stellar and Gas Disk Potentials)
   - fitting: _not stated_
   - validation: _not stated_
4. **Rescale the H I rotation curve to CO and the stellar component to the maximum disk**: Multiply V_HI by f_HI to match the CO rotation velocity in the outer CO coverage, merge CO and scaled H I curves; scale V_star by f_star so the baryonic contribution equals 0.85 V_c at 2.2 l_star  
  > "we scale the entire H I rotation curve by a multiplicative factor" (3.2 Rescaling of the H I Rotation Curves and the Stellar Potential); "such that it matches the CO rotation velocity in the outer part of the CO radial coverage to ensure continuity" (3.2 Rescaling of the H I Rotation Curves and the Stellar Potential)
   - parameter: Anchoring radius 2.2 l_star; total baryonic contribution normalised to 0.85 of V_c  
  > "The choice to normalize the total baryonic contribution to 0.85 times the dynamical mass implied by the circular velocity is empirically determined in previous studies (cite: maximaldisk)." (3.2 Rescaling of the H I Rotation Curves and the Stellar Potential)
   - parameter: H I points weighted proportionally to their larger radial bin width in the hybrid curve  
  > "we also assign proportionally larger weights to each of the H I data points when using the hybrid rotation curves in further analyses" (Footnote 1)
   - assumption: Maximum disk; CO-based inclinations are the internally consistent anchor  
  > "is determined for each galaxy from the classic maximum disk assumption (cite: maximaldisk)" (3.2 Rescaling of the H I Rotation Curves and the Stellar Potential); "Here we use the CO-based results as our “anchoring points” for internal consistency" (3.2 Rescaling of the H I Rotation Curves and the Stellar Potential)
   - fitting: _not stated_
   - validation: Adopting alternative M/L ratios between 0.2 and 0.6 does not change the main results qualitatively  
  > "we have verified that adopting any reasonable alternative M/L ratio (e.g., between 0.2 and 0.6) would not change our main results on a qualitative level." (4.1 Rotation Curve Decomposition)
5. **Fit an NFW dark matter halo to the rotation curve**: Fit V_c^2 = V_star,scaled^2 + V_gas^2 + V_DM^2 with a cumulative NFW V_DM; compare a two-parameter (free R_s) and a one-parameter (R_s = 9 H_star) model using BIC; fit excludes bar and central-structure radii  
  > "We use the Bayesian information criterion (BIC) to determine which model best fits the rotation curve of each galaxy." (3.3 Rotation Curve Fitting); "the fit ignores all measurements in the radius range covered by a stellar bar or a central stellar structure" (4.1 Rotation Curve Decomposition)
   - parameter: Free parameters rho_0 and R_s (stellar and gas components have no free parameters)  
  > "In this model, the stellar and gas components do not have free parameters" (3.3 Rotation Curve Fitting)
   - assumption: Spherically symmetric NFW halo  
  > "we assume the dark matter halos follow a spherically symmetric, Navarro-Frenk-White profile (cite: NFW)" (3 Methodology)
   - fitting: Model comparison by BIC; sampler, priors and likelihood not stated  
  > "We use the Bayesian information criterion (BIC) to determine which model best fits the rotation curve of each galaxy." (3.3 Rotation Curve Fitting)
   - validation: Visual comparison of model and rotation curves; two galaxies with limited radial coverage flagged for caution  
  > "We find the combination of the rescaled stellar component, the gas component, and the NFW dark matter component can fit the joint CO-H I rotation curve very well, especially outside the bar and/or center region." (4.1 Rotation Curve Decomposition)
6. **Solve for the equilibrium gas scale height**: Solve the cubic vertical-equilibrium equation for H_gas at each radius, using sigma_eff, Sigma_gas, Sigma_star, Omega_DM and H_star, for five H_star assumptions; GP smoothing of sigma_eff  
  > "we consider five different assumptions both for calculating the stellar disk potential in" (3.4 Disk Scale Height); "we perform a Gaussian process regression also on the $\sigma_\mathrm{eff}$ profiles to suppress small-scale fluctuations" (3.4 Disk Scale Height)
   - parameter: zeta ~ 1/3  
  > "$\zeta \approx 1/3$ is a geometric factor that is insensitive to the exact vertical distribution of the gas density" (3.4 Disk Scale Height)
   - parameter: H_star options: 0.27 l_star, 0.09 l_star, H_star = H_gas, 800 pc, 300 pc  
  > "A constant value of $H_\star = 800$ pc." (3.4 Disk Scale Height); "An alternative constant value, $H_\star = 300$ pc." (3.4 Disk Scale Height)
   - assumption: Exponential vertical profiles; magnetic contribution to sigma_eff not included  
  > "is exact if the gas disk and stellar disk both have exponential profiles along the vertical direction" (3.4 Disk Scale Height); "This does not take into account the magnetic contribution to" (Footnote 3)
   - fitting: _not stated_
   - validation: Compared with Milky Way and edge-on galaxy scale heights  
  > "Our results also seem to agree with previous extragalactic studies" (4.2 Disk Scale Heights)
7. **Compute the gas equilibrium weight**: Sum gas, stellar and dark matter weight terms W_gas + W_star + W_DM using H_gas from step 6; compare with the commonly used approximation  
  > "The total weight of the gas per unit area is the sum of these terms" (3.5 Gas Equilibrium Weight); "While in most cases the two options give almost identical results, in a few cases they can deviate on a non-trivial level." (4.3 Gas Equilibrium Weight)
   - assumption: Vertical dynamical equilibrium: weight balanced by the average midplane gas pressure  
  > "which should be balanced by the average gas pressure near the disk midplane under the assumption of vertical dynamical equilibrium" (3.5 Gas Equilibrium Weight)
   - fitting: _not stated_
   - validation: Comparison against the approximate formula and five H_star assumptions  
  > "We also test the impact of gas weight calculation with different formulae in" (4.3 Gas Equilibrium Weight)
8. **Compare weight with SFR surface density**: Compare W versus Sigma_SFR (Sun et al. 2023 SFR measurements) with the Ostriker-Kim power-law relation from TIGRESS  
  > "predicts the following power-law relation based on the TIGRESS simulations" (4.4 Gas Weight and Star Formation)
   - assumption: Weight equals total pressure in equilibrium  
  > "the gas weight (which in equilibrium balances total pressure" (4.4 Gas Weight and Star Formation)
   - fitting: _not stated_
   - validation: Scatter of W-Sigma_SFR relation with and without the f_star scaling  
  > "rms scatter decreases from 0.18 to 0.16 dex" (4.4 Gas Weight and Star Formation)

## Software

- **3D-Barolo** 1.7: H I tilted-ring kinematic modeling of PHANGS-VLA cubes  
  > "we perform similar kinematic modeling with 3D-Barolo (version 1.7) on the PHANGS–VLA H I data cubes" (2.4 CO and H I Kinematic Measurements)
- **MegaTable** 4.0: Listed in Software section; specific use not stated  
  > "`MegaTable` (cite: MegaTable_4.0)" (Software)
- **NumPy** : Listed in Software section; specific use not stated  
  > "`NumPy` (cite: NumPy_2020)" (Software)
- **SciPy** : Listed in Software section; specific use not stated  
  > "`SciPy` (cite: SciPy_2020)" (Software)
- **Astropy** : Listed in Software section; specific use not stated  
  > "`Astropy` (cite: Astropy2013; Astropy2018; AstroPy_2022)" (Software)
- **Scikit-learn** : Listed in Software section; specific use not stated  
  > "`Scikit-learn` (cite: Sklearn_2011)" (Software)
- **hankel** : Listed in Software section; specific use not stated  
  > "`hankel` (cite: Murray2019)" (Software)
- **Pandas** : Listed in Software section; specific use not stated  
  > "`Pandas` (cite: Pandas_2020)" (Software)
- **Matplotlib** : Listed in Software section; specific use not stated  
  > "`Matplotlib` (cite: Matplotlib_2007)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| GP smoothing length scale, stellar profiles | 3 | not stated | kpc | 2 | the optimal length scales for the stellar and gas profiles are 3 kpc and 1.5 kpc, respectively |
| GP smoothing length scale, gas profiles | 1.5 | not stated | kpc | 2 | the optimal length scales for the stellar and gas profiles are 3 kpc and 1.5 kpc, respectively |
| H I rotation curve scaling factor f_HI (most galaxies, range) | 0.94-1.19 | not stated | dimensionless | 4 | The $f_\mathrm{HI}$ values for most galaxies are in the range of $0.94{-}1.19$ |
| Typical size of H I rescaling correction |1 - f_HI| | <~10% | not stated | dimensionless | 4 | typically $/1-f_\mathrm{HI}/\,{\lesssim}\,10\%$ |
| Stellar scaling factor f_star range for 13 of 17 galaxies (H_star = 0.27 l_star) | 0.8-1.5 | not stated | dimensionless | 4 | 13 out of 17 galaxies have $f_\star$ values between $0.8{-}1.5$ |
| Stellar scaling factor f_star range for the remaining four galaxies | 1.6-2.1 | not stated | dimensionless | 4 | The remaining four galaxies have $f_\star$ values of $1.6{-}2.1$ |
| Implied modified 3.6 micron M/L ratio, median and 1 sigma range across sample | 0.47 +/- 0.14 | 1 sigma range 0.14 | Msun / Lsun,3.6um | 4 | $0.47\pm0.14\;M_\odot\,L_\mathrm{\odot,3.6\mu m}^{-1}$ across our sample |
| Gas scale height H_gas, inner to outer disk | <~100 pc inner disks to >500 pc at large radii | not stated | pc | 6 | We find the gas scale height $H_\mathrm{gas}$ increases from ${\lesssim}100$ pc in the inner disks to ${>}500$ pc at large radii |
| Change in H_gas when H_star varies by a factor of 3 | 30-40% | not stated | percent | 6 | with $H_\mathrm{gas}$ varying by 30–40% when $H_\star$ varies by a factor of 3 |
| Radius where H_gas exceeds H_star in NGC 4781 for H_star = 0.27 l_star | ~4 | not stated | kpc | 6 | $H_\mathrm{gas}$ exceeds $H_\star$ at $r\approx4$ kpc when assuming $H_\star=0.27\ell_\star$ |
| Radius where H_gas exceeds H_star in NGC 4781 for H_star = 0.09 l_star | ~2 | not stated | kpc | 6 | but it happens at $r\approx2$ kpc when assuming $H_\star=0.09\ell_\star$ |
| Typical H_gas range over several scale lengths (H_star = 0.27 l_star) | 100-500 | not stated | pc | 6 | Most galaxies have $H_\mathrm{gas}$ in the range of 100–500 pc over several disk scale lengths. |
| Radius beyond which gas weight term dominates (many galaxies) | 3-6 l_star | not stated | l_star | 7 | for many galaxies, the gas component becomes dominant beyond $3{-}6\;\ell_\star$ |
| Radius beyond which dark matter weight term dominates (some galaxies) | 5-8 l_star | not stated | l_star | 7 | for some, we even see the dark matter component taking over beyond $5{-}8\;\ell_\star$ |
| Dark matter exceeds stellar contribution to V_c at radius | R ~ 3-5 l_star | not stated | l_star | 5 | dark matter contribution to the circular velocity often exceeds the stellar contribution at $R\approx3{-}5\,\ell_\star$ |
| rms scatter of W-Sigma_SFR relation with f_star scaling versus unscaled | 0.16 versus 0.18 | not stated | dex | 8 | rms scatter decreases from 0.18 to 0.16 dex |
| Change in predicted SFR surface density from choice of H_star in inner disk | up to ~60% | not stated | percent | 8 | can change the predicted SFR by up to $\sim 60\%$ in the inner disk |

## Qualitative findings

- Gas gravity is a negligible contribution to the circular velocity at all radii  
  > "For all galaxies, the gas gravity has a negligible contribution to the circular velocity at all radii" (4.1 Rotation Curve Decomposition)
- The weight approximation commonly used in the literature can fail when gas and stellar scale heights become comparable, mostly in H I-dominated outer disks  
  > "While in most cases the two options give almost identical results, in a few cases they can deviate on a non-trivial level." (4.3 Gas Equilibrium Weight)

## Claim tuples

- H: A joint stellar-gas-NFW dark matter model can account for the CO+H I rotation curves of the 17 galaxies | E: Merge CO and rescaled H I curves, rescale stellar contribution by the maximum disk condition, fit NFW halo outside bar/center | R: The three-component model fits the joint rotation curve well outside bar and central regions; f_star between 0.8 and 1.5 for 13 of 17 galaxies per the text | F: A reasonable decomposition is obtained only after rescaling H I and stellar components | **supported**
- H: How does the equilibrium gas scale height vary with radius? | E: Solve the vertical equilibrium cubic equation for H_gas at each radius for each galaxy | R: H_gas rises from <~100 pc in inner disks to >500 pc at large radii | F: Consistent with the Milky Way and edge-on galaxies | **supported**
- H: Gas scale height and weight depend on the assumed stellar disk scale height | E: Repeat calculations for five H_star assumptions | R: H_gas changes by 30-40% in the inner disk when H_star changes by a factor of 3, and less than 10% in the outer disk | F: Inner-disk H_gas, weight and predicted SFR are sensitive to the H_star assumption | **supported**
- H: The commonly used approximate weight formula is adequate | E: Compare the full weight equations with the H_gas << H_star approximation | R: Nearly identical in most cases but non-trivial deviations in a few | F: Authors advocate the full formulation, especially in H I-dominated outer disks | **partially**
- H: Gas weight versus Sigma_SFR follows the PRFM (Ostriker-Kim) prediction | E: Compare refined weights with Sun et al. 2023 SFR surface densities and the TIGRESS-based relation | R: Agreement for H_star = 0.27 l_star; slope shallower than simulations at high pressure; scatter 0.18 to 0.16 dex with f_star scaling | F: Overall agreement with theory and prior observations with a mildly shallower slope | **partially**

## Reasoning

- Why this data: Sample has high-quality multiwavelength coverage including PHANGS-ALMA CO imaging  
  > "These galaxies all have high-quality, multiwavelength coverage, in particular CO line imaging from PHANGS–ALMA (cite: Leroy2021)" (Introduction)
- Why this method: NFW profile adopted to obtain a smooth dark matter potential  
  > "To obtain a smooth dark matter potential, we assume the dark matter halos follow a spherically symmetric, Navarro-Frenk-White profile (cite: NFW)." (3 Methodology)
- Alternative: Two-parameter NFW (free R_s) versus one-parameter NFW (fixed R_s = 9 H_star), chosen per galaxy by BIC  
  > "we compare the fitting results between a two-parameter model with varying $R_s$ and a one-parameter model" (3.3 Rotation Curve Fitting)
- Alternative: Alternative M/L ratios between 0.2 and 0.6 tested and found not to change results qualitatively  
  > "we have verified that adopting any reasonable alternative M/L ratio (e.g., between 0.2 and 0.6) would not change our main results on a qualitative level." (4.1 Rotation Curve Decomposition)
- How they decided it was enough: GP length scales chosen by testing several and visual inspection  
  > "We test different length scales on our data and visually inspect the outcomes" (3.1 Stellar and Gas Disk Potentials)
- Limitation (authors): Analysis cannot confirm or rule out the maximal disk scenario  
  > "We note that our analyses cannot conclusively confirm or rule out the maximal disk scenario." (4.1 Rotation Curve Decomposition)
- Limitation (authors): NFW fit results for NGC 1385 and NGC 4571 are uncertain because of limited radial coverage  
  > "Their dark matter NFW profile fit results should be taken with caution." (Table 2 notes)
- Limitation (authors): Magnetic contribution to sigma_eff ignored, which could raise it by ~30%  
  > "This does not take into account the magnetic contribution to" (Footnote 3)
- Limitation (authors): Gas scale height cubic equation is exact only for exponential vertical profiles and accurate to ~25% otherwise  
  > "is correct within $\sim 25\%$ more generally (cite: Hassan_etal_2024)" (3.4 Disk Scale Height)
- Caveat (inferred, ours): Text says 13 of 17 galaxies have f_star of 0.8-1.5 and four have 1.6-2.1, but Table 2 (H_star = 0.27 l_star) lists about eight values in 0.8-1.5, eight above 1.5 (up to 2.46 for NGC 3137) and one below 0.8 (NGC 3507, 0.67); table and text disagree and the table caption says f_star scales Sigma_star while the text applies it to V_star
- Caveat (inferred, ours): f_star and f_HI absorb distance, inclination and M/L errors simultaneously, so the dark matter halo parameters depend on the maximum disk assumption
- Caveat (inferred, ours): ALMA contributes only through previously published profiles and rotation curves; no ALMA calibration or imaging is done here
- Caveat (inferred, ours): No uncertainties are propagated on H_gas, weight or NFW parameters

## Reproducibility

- Data public (paper): Spitzer S4G images stated as made public; public status of the ALMA and VLA products is not stated in the paper  
  > "some processed and made public as part of the S$^4$G survey" (2.1 Near-IR Data Tracing Stellar Distribution)
- Products in archive: _not stated_
- Missing: Per-galaxy radial profile tables and rotation curves (must be fetched from Sun et al. 2022 / MegaTable and Lang et al. 2020)
- Missing: GP kernel hyperparameters beyond length scale, and exclusion radii for bars and centers
- Missing: NFW fitting optimiser, weighting and uncertainties
- Missing: 3D-Barolo configuration for PHANGS-VLA cubes
- Missing: No released analysis code for this paper is stated
- Data volume (inferred): Small (megabytes): radial profile tables and rotation curves only; no ALMA visibilities or cubes needed
- Score (inferred): 3/5, Equations and most assumptions are given and results are numeric, but inputs come from earlier papers' tables and the fitting and smoothing details are incomplete; ALMA data are reached only through derived products.
- Rediscovery candidate: no, ALMA plays a supporting role through published products and several fit and smoothing settings are unstated, so a faithful redo depends on external tables and guesses.

## Links

- Method: Sun et al. 2022 (cite: Sun2022) (Radial profiles of stellar, atomic and molecular surface density and velocity dispersion)
- Method: Leroy et al. 2021 (cite: Leroy2021) (PHANGS-ALMA CO(2-1) survey and galaxy parameters)
- Method: Lang et al. 2020 (cite: rotation) (CO rotation curves and orientation parameters)
- Method: Chiang et al. 2024 (cite: Chiang_etal_2024) (PHANGS-VLA H I data)
- Method: Hassan et al. 2024 (cite: Hassan_etal_2024) (Cubic equation for gas scale height and weight formulae)
- Method: Di Teodoro et al. 2023 (cite: DiTeodoro+2023) (3D-Barolo modeling procedure)
- Method: Schinnerer & Leroy 2024 (cite: Schinnerer_Leroy_2024) (alpha_CO prescription)
- Companion: Sun et al. 2020 (cite: Sun2020) (Earlier PHANGS pressure and weight analysis using the approximate formula)
- Companion: Sun et al. 2023 (cite: Sun_etal_2023) (Previous weight versus SFR surface density comparison and SFR measurements)
- Companion: Ostriker & Kim 2022 (cite: 2022ApJ...936..137O) (PRFM theory and TIGRESS SFR-weight relation)
- Related: PHANGS-ALMA
- Related: PHANGS-VLA
- Related: THINGS
- Related: S4G
- Related: PHANGS MegaTable

## Checks

```json
{
 "quotes": 123,
 "quotes_ok": 123,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 124,
  "stated": 81,
  "rate": 0.653
 },
 "evidence_ok": true
}
```
