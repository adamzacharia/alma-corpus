# The two-dimensional pressure structure of the HD 163296 protoplanetary disk as probed by multi-molecule kinematics

`2025A&A...694A.108P` | Astronomy and Astrophysics 2025 | first author: Pezzotta, V. | arXiv: 2501.05517 | DOI: 10.1051/0004-6361/202451307

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Whether the vertical (2D) thermal stratification of the HD 163296 disk is detectable in the rotation curves of seven molecular tracers, and what disk mass, scale radius and 2D pressure structure follow from a multi-molecule stratified fit  
  > "testing whether vertical stratification can be detected in the kinematic structure of the disk, probed through multiple tracers located at different heights above the midplane" (Introduction); "our aim is to provide an accurate estimate of the disk mass and scale radius, based on a multi-molecule fit of the curves with a thermally stratified model" (Introduction)
- Target **HD 163296**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01055.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.15'' for 12CO, 13CO, C18O, HCN, C2H (per Table 1); 0.3'' for H2CO and HCO+ (the two lower-resolution lines)  
  > "the two lines with lower resolution data ($0.3''$)" (3.1 Molecular optical depth profiles)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Public MAPS ALMA Large Program data (archival reuse)  
  > "we based our work on the publicly available high spatial and spectral resolution data provided by the MAPS ALMA Large Program" (2.2 Targeted emission lines)
- Line: 12CO J=2-1 (230.538000 GHz)
- Line: 13CO J=2-1 (220.398684 GHz)
- Line: C18O J=2-1 (219.560354 GHz)
- Line: HCN J=3-2, F=3-2 (265.886434 GHz)
- Line: H2CO 3_03-2_02 (218.222192 GHz)
- Line: HCO+ J=1-0 (89.188525 GHz)
- Line: C2H N=3-2, J=5/2-3/2, F=3-2 (262.064986 GHz)
- External data: 2D gas kinetic temperature structure T(R,z) (Dullemond et al. 2020 parameterization, seven fitted parameters in Table 1: T_atm,0=63 K, q_atm=-0.61, T_mid,0=24 K, q_mid=-0.18, alpha=3.01, z0=9 au, beta=0.42)  
  > "we use the kinetic temperature by (cite: maps4) and the observed brightness temperature from the data" (3.1 Molecular optical depth profiles) [from (cite: maps4); parameterization from (cite: dullemond2020)]
- External data: Parametric emitting-layer fits z(R) for each molecule (Z0, phi, r_taper, psi in Table 2), plus nonparametric emitting layers  
  > "Best-fit parameters for the molecular emitting layers for HD 163296 fitted by (cite: paneque)." (Table 2); "adopting nonparametric emitting layers for all the molecules, as retrieved by (cite: paneque)" (4.2 Dependence on the emitting layers) [from (cite: paneque)]
- External data: Disk geometry: i=46.7 deg, PA=313.3 deg  
  > "We assumed $i=46.7$°, $PA=313.3$° from (cite: maps1)" (3.2 Rotation curves extraction) [from (cite: maps1)]
- External data: Hyperfine frequency shifts: 2.5 MHz (C2H), 2.09 MHz and 1.54 MHz (HCN)  
  > "Cologne Database for Molecular Spectroscopy (CDMS)" (3.2.2 Multi-Gaussian methods); "$\Delta \nu = 2.5$ MHz (between the two transitions)" (3.2.2 Multi-Gaussian methods) [from (cite: sastry1981; muller2000) and (cite: ahrens2002), via CDMS]
- External data: Isothermal comparison model: H/R=0.084 and q=-0.84  
  > "with $H/R=0.084$ and $q=-0.84$ (cite: maps5)" (4.1 Multi-molecule fit) [from (cite: maps5)]
- External data: Two-molecule stratified fit results (M_star, M_d, R_c) used for comparison in Table 3  
  > "We also compare our results with the ones obtained by (cite: martire)" (4.1 Multi-molecule fit) [from (cite: martire)]

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

- ALMA data are the public MAPS Large Program cubes (calibration and imaging done by MAPS)  
  > "we based our work on the publicly available high spatial and spectral resolution data provided by the MAPS ALMA Large Program (cite: maps1)" (2.2 Targeted emission lines) [from (cite: maps1)]
- Rotation curve extraction method (SHO in eddy)  
  > "we used the eddy Python package (cite: teague_eddy), following the method presented in (cite: teague2018a) and (cite: teague2018b)" (3.2 Rotation curves extraction) [from (cite: teague_eddy); (cite: teague2018a); (cite: teague2018b)]
- 2D thermal structure of the disk  
  > "we assume the 2D thermal structure of the disk from (cite: maps4) and the molecular emitting layers $z(R)$ from (cite: paneque)" (3 Methods) [from (cite: maps4)]
- Molecular emitting layers z(R)  
  > "we assume the 2D thermal structure of the disk from (cite: maps4) and the molecular emitting layers $z(R)$ from (cite: paneque)" (3 Methods) [from (cite: paneque)]
- Stratified rotation-curve model and its f, g parameterization  
  > "We adopt the model for our rotation curves fit from (cite: martire)" (3.3 Vertically stratified model) [from (cite: martire)]
- Fitting procedure (same as in the earlier two-molecule fit)  
  > "We point out that the fitting procedure in the two works is the same" (4.1 Multi-molecule fit) [from (cite: martire)]
- Isothermal model expression  
  > "The adopted expression for the isothermal model is explained in (cite: lodato), Eqs. 12-14." (3.3 Vertically stratified model) [from (cite: lodato), Eqs. 12-14]
- Surface density profile (self-similar solution)  
  > "We consider a disk surface density as described by the self-similar solution of (cite: lyndenbell)" (3.3 Vertically stratified model) [from (cite: lyndenbell)]

### Not stated but needed to reproduce (our reading)

- Exact MAPS data products used (which cube versions, weighting/robust, uv taper, channel width, continuum subtraction, JvM correction, file names)
- Distance to HD 163296 and systemic velocity adopted
- Radial range, annulus width and number of spectra per annulus used in the eddy extractions, and how the 20 independent subsamples were drawn
- Version of eddy and whether the new multi-Gaussian hyperfine fit is in a public release
- Priors, parameter bounds, initial walker positions and likelihood form (including how rotation-curve errors enter) in the DySc fit for M_star, M_d, R_c
- Radial range of the rotation curves entering the fit and how bad radii (H2CO emission gap near 150 au) were masked
- Value of q used inside the stratified model and the definition of f and g used numerically
- S/N threshold and procedure for the initial visual selection of lines
- Version of DySc and emcee
- Which hyperfine components and rest frequencies were used for HCN and C2H when converting shifts to velocity

## Analysis recipe

1. **Select molecular lines from the MAPS cubes**: Visual cube exploration; lines chosen by brightness and high S/N  
  > "An initial visual datacube exploration was performed for each molecule in order to select suitable lines: the candidates were chosen according to their brightness and high signal-to-noise ratio." (2.2 Targeted emission lines)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive molecular optical depth profiles to check emitting layers**: Radial surface brightness from the data compared with the optically thick Planck brightness at the assumed emitting layer; tau = -ln(1 - I_data/I_Planck)  
  > "we calculate the expected surface brightness profile $I_\mathrm{Planck}$ at the emitting layer, under the assumption of optically thick emission, through the Planck law" (3.1 Molecular optical depth profiles)
   - software: GoFish
   - parameter: 30 deg wedge along the disk major axis for the radial profile  
  > "where we set a $30$° wedge along the disk major axis" (3.1 Molecular optical depth profiles)
   - assumption: Kinetic temperature at the emitting layer from the Dullemond et al. (2020) T(R,z) with MAPS parameters; LTE, optically thick reference emission  
  > "We adopt the molecular emitting layers by (cite: paneque) into Eq." (3.1 Molecular optical depth profiles)
   - fitting: _not stated_
   - validation: Compared tau with independent optical depth estimates from other works  
  > "We assess that our test provides the expected results, in agreement with optical depth estimates obtained with independent methods" (3 Methods)
3. **Extract rotation curves with eddy (SHO method)**: Fit each spectrum with a Gaussian to get its centroid, then fit centroids in each annulus with a cosine (harmonic) function to get v_theta  
  > "we fit each spectrum with a Gaussian curve to identify the intensity peak and the corresponding velocity, and then we proceed to the fit of the line centroids with the harmonic function" (3.2 Rotation curves extraction)
   - software: eddy
   - parameter: i=46.7 deg, PA=313.3 deg, zero center offsets  
  > "We assumed $i=46.7$°, $PA=313.3$° from (cite: maps1)" (3.2 Rotation curves extraction)
   - parameter: Extraction repeated 20 times with independent spectrum samples; uncertainty = weighted standard deviation  
  > "For each tracer we repeat the extraction of the rotation curve $20$ times" (3.2 Rotation curves extraction); "we compute the uncertainties on the velocity values as their weighted standard deviation" (3.2 Rotation curves extraction)
   - assumption: Exponentially tapered power-law emitting layers z(R) with Paneque et al. parameters; azimuthal symmetry; front side dominates  
  > "For the molecular emission layers we assumed an exponentially tapered power law" (3.2 Rotation curves extraction); "eddy does not distinguish the upper and lower surfaces of disks, and assumes that the front side dominates over the back side" (3.2.1 Limitations of the method)
   - fitting: _not stated_
   - validation: Compared with discminer curves of Martire et al.: differences <4% and <5% for two lines; flat vs elevated emission test  
  > "We measure very low differences, which are $<4\%$ for and $<5\%$ for" (3.2.1 Limitations of the method)
4. **Rotation curves of hyperfine lines (C2H, HCN)**: New multi-Gaussian (double for C2H, triple for HCN) spectrum fit in eddy with shared width and fixed hyperfine velocity shifts  
  > "we implemented in eddy a new fitting procedure for hyperfine lines using multiple Gaussian components (two or three, depending on the number of hyperfine transitions)" (3.2.2 Multi-Gaussian methods)
   - software: eddy, CDMS
   - parameter: Equal Gaussian width for all components  
  > "where the width of the multiple Gaussians is assumed to be the same" (3.2.2 Multi-Gaussian methods)
   - parameter: Fixed shifts: 2.5 MHz (C2H), 2.09 and 1.54 MHz (HCN); sigma bounded to half the component separation; intensity ratio priors xi in [0.2,1.5] (C2H) and [0.1,1] (HCN)  
  > "the width of the Gaussians is not larger than half of the distance in velocity between the two considered transitions" (3.2.2 Multi-Gaussian methods)
   - fitting: Free parameters: v0, sigma, I0, xi (C2H); v0, sigma, I0, xi_blue, xi_red (HCN); Keplerian curve used as starting guess for v0 for C2H  
  > "we computed the Keplerian velocity at each radius $R$ and azimuthal angle $\theta$" (3.2.2 Multi-Gaussian methods)
   - validation: Compared multi-Gaussian curves with single-Gaussian eddy curves  
  > "These methods lead to a remarkable improvement in the extraction of the rotation curves of hyperfine structured lines." (3.2.2 Multi-Gaussian methods)
5. **Test beam smearing in rotation curves**: Correlate radial intensity gradient of the line with the velocity difference between C2H (or HCN) and 12CO rotation curves  
  > "We find a strong anticorrelation between the two following measurable quantities as a function of radius (evaluated at the same radii)" (3.2.3 Beam smearing effect)
   - assumption: 12CO curve used as smooth Keplerian reference  
  > "the $^{12}$CO curve was chosen as reference because it exhibits a typical smooth Keplerian profile" (3.2.3 Beam smearing effect)
   - fitting: _not stated_
   - validation: _not stated_
6. **Simultaneous multi-molecule fit of the seven curves with the stratified model**: MCMC maximisation of the likelihood of one stratified rotation-curve model fitted to all seven curves for M_star, M_d, R_c  
  > "the code performs the fit of the data to the model by maximizing the likelihood of the model, with the posterior distribution explored by Monte Carlo Markov Chains, as implemented in emcee" (3.3 Vertically stratified model)
   - software: DySc, emcee
   - parameter: 200 walkers, 1000 burn-in steps, 2000 steps  
  > "We ran the MCMC exploration using 200 walkers, 1000 burn-in steps and 2000 steps to determine the final posterior distribution of the fitted parameters." (4.1 Multi-molecule fit)
   - parameter: 95% credibility intervals used as uncertainties  
  > "For each parameter, we compute a 95% credibility interval" (4.1 Multi-molecule fit)
   - assumption: gamma = 1 in the surface density; temperature structure fixed from MAPS (uncertainties not propagated); emitting layers from Paneque et al.  
  > "we adopt $\gamma=1$" (3.3 Vertically stratified model); "In this work we did not account for the uncertainties in the temperature structure of the disk." (4.1 Multi-molecule fit)
   - fitting: emcee MCMC; priors not stated  
  > "the code DySc" (3.3 Vertically stratified model)
   - validation: Fit repeated adding one molecule at a time (reduced chi2 normalised to maximum); compared with isothermal 7-molecule fit and with Martire et al. 2-molecule fit  
  > "we fitted the rotation curves starting with two molecules and then progressively adding one molecule at a time" (4.1 Multi-molecule fit)
7. **Map the 2D pressure structure**: Combine fitted disk mass and scale radius with the assumed T(R,z) to compute P(R,z)  
  > "we can show the normalized 2D pressure structure of the disk" (4.1 Multi-molecule fit); "is determined by the values for the disk mass and scale radius obtained by the fit of the rotation curves" (4.1 Multi-molecule fit)
   - assumption: Barotropic fluid; shape of P(R,z) set by the assumed temperature structure  
  > "considering a barotropic fluid, the 2D pressure in the disk is given by" (3.3 Vertically stratified model)
   - fitting: _not stated_
   - validation: _not stated_
8. **Compare stratified and isothermal predictions of velocity differences vs C18O**: Normalised difference of squared rotation velocities of each molecule relative to C18O, compared with isothermal and stratified model predictions  
  > "We compare squared rotation velocities of each molecule with the one, and we illustrate the expected behavior of their normalized difference in the isothermal and in the vertically stratified scenarios." (4.1 Multi-molecule fit)
   - parameter: Isothermal model with H/R=0.084 and q=-0.84  
  > "with $H/R=0.084$ and $q=-0.84$ (cite: maps5)" (4.1 Multi-molecule fit)
   - fitting: _not stated_
   - validation: Stratified model reproduces observed differences; isothermal does not  
  > "it is clear that the thermally stratified prediction is more appropriate to describe the observed differences between the two rotation curves, while the isothermal model cannot reproduce the observed behavior" (4.1 Multi-molecule fit)
9. **Test dependence on the assumed emitting layers**: Repeat extraction and multi-molecule fit with (a) flat midplane emission for all molecules and (b) nonparametric emitting layers  
  > "we repeated the whole identical routine of rotation curves extraction and multi-molecule fit of the curves, considering flat emission for all the molecules" (4.2 Dependence on the emitting layers); "we repeated the whole analysis adopting nonparametric emitting layers for all the molecules" (4.2 Dependence on the emitting layers)
   - software: eddy, DySc
   - fitting: Same MCMC setup (200, 1000, 2000)  
  > "All the fits were performed with the same number of walkers, burn-in steps, and steps (200, 1000, 2000)." (4.1 Multi-molecule fit)
   - validation: Differences in M_star, M_d, R_c compared with the parametric case and with literature systematics (~25% in disk mass)  
  > "The difference we measure for the disk mass estimate is in agreement with the results by (cite: veronesi2024) and (cite: andrews2024), predicting an uncertainty close to $\sim 25 \%$." (4.2 Dependence on the emitting layers)

## Software

- **eddy** : Rotation curve extraction (SHO method), extended here with a multi-Gaussian hyperfine fit  
  > "we used the eddy Python package (cite: teague_eddy)" (3.2 Rotation curves extraction)
- **GoFish** : Radial surface brightness profiles (radial_profile) for optical depth  
  > "using the GoFish (cite: Teague_GoFish) function" (3.1 Molecular optical depth profiles)
- **DySc** : Simultaneous multi-molecule fit of rotation curves for M_star, M_d, R_c  
  > "To perform the simultaneous fit of the rotation curves, we use the code DySc" (3.3 Vertically stratified model)
- **emcee** : MCMC sampler inside DySc  
  > "with the posterior distribution explored by Monte Carlo Markov Chains, as implemented in emcee" (3.3 Vertically stratified model)
- **discminer** : Used by Martire et al. to extract rotation curves compared with eddy curves  
  > "the authors retrieve the rotation curves using" (4.1 Multi-molecule fit)
- **CDMS** : Hyperfine transition frequency shifts  
  > "Cologne Database for Molecular Spectroscopy (CDMS)" (3.2.2 Multi-Gaussian methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar mass, stratified 7-molecule fit | 1.8905 | 0.0002 (95% credibility interval extremes) | Msun | 6 | $1.8905 \pm 0.0002$ |
| Disk mass, stratified 7-molecule fit | 0.1161 | 0.0003 | Msun | 6 | $0.1161 \pm 0.0003$ |
| Scale radius R_c, stratified 7-molecule fit | 143.1 | 0.1 | au | 6 | $143.1 \pm 0.1$ |
| Disk mass, isothermal 7-molecule fit | 0.1565 | 0.0003 | Msun | 6 | $0.1565 \pm 0.0003$ |
| Scale radius R_c, isothermal 7-molecule fit | 48.1 | 0.1 | au | 6 | $48.1 \pm 0.1$ |
| Stellar mass, isothermal 7-molecule fit | 1.8905 | 0.0002 | Msun | 6 | the estimate of the stellar mass does not change between the isothermal and stratified fits |
| Stellar mass, flat-emission test | 1.7827 | 0.0003 | Msun | 9 | $M_\star=1.7827\pm 0.0003$ M$_\odot$ |
| Disk mass, flat-emission test | 0.1396 | 0.0003 | Msun | 9 | $M_\text{d}=0.1396\pm 0.0003$ M$_\odot$ |
| Scale radius, flat-emission test | 174.8 | 0.3 | au | 9 | $R_\text{c}=174.8\pm 0.3$ au |
| Nonparametric vs parametric layers: M_d difference | <~30% | not stated | percent | 9 | $\lesssim 1\%$ for $M_\star$, $\lesssim 30\%$ for $M_\text{d}$, and $\lesssim 13\%$ for $R_\text{c}$ |
| Peak optical depths of the two optically thin lines (molecule names missing in text) | 0.11 and 0.45 | not stated | dimensionless | 2 | reaching maximum peaks at $\tau \sim 0.11$ and $\tau \sim 0.45$ respectively |
| HCN intensity peak radius | 109 | not stated | au | 2 | a local maximum around the radius of the intensity peak ($R=109$ au) |

## Qualitative findings

- Thermal stratification leaves a measurable imprint in kinematics across the whole vertical extent, including layers near the midplane  
  > "Temperature leaves a clear imprint in the kinematics of molecular lines originating from the whole vertical extent of the disk" (4.1 Multi-molecule fit)
- Beam smearing produces velocity deviations of opposite sign to pressure-gradient deviations  
  > "we note that beam smearing works in an opposite way to pressure gradients" (3.2.3 Beam smearing effect)
- Rotation curves can trace pressure substructure with a vertical dependence  
  > "This indicates that rotation curves can be a powerful tool to characterize the 3D structure of gaps, which should be further investigated in the future." (4.1 Multi-molecule fit)
- Adding molecules reduces chi2 and shrinks the posterior; largest improvement going from two to three molecules  
  > "the most significant improvement is achieved with the inclusion of in the fit, going from two to three molecules" (4.1 Multi-molecule fit)

## Claim tuples

- H: Vertical thermal stratification is detectable in the rotation curves of tracers at different heights, including near the midplane | E: Fit seven rotation curves simultaneously with a stratified and an isothermal model, and compare normalised squared-velocity differences relative to C18O | R: Stratified model R_c=143.1 au vs isothermal 48.1 au; stratified prediction matches the observed velocity differences, isothermal does not | F: Thermal stratification must be included to reproduce velocity differences at distinct heights | **supported**
- H: A multi-molecule stratified fit gives accurate dynamical estimates of M_star, M_d and R_c | E: DySc MCMC fit of seven eddy rotation curves with the stratified model | R: M_star=1.8905, M_d=0.1161 Msun, R_c=143.1 au (formal errors underestimated) | F: Multi-molecule stratified fits can be performed efficiently and constrain these parameters | **supported**
- H: Multi-Gaussian fits improve rotation curves of hyperfine-split lines | E: Implemented double- and triple-Gaussian spectrum fits in eddy for C2H and HCN and compared with single-Gaussian | R: Smooth, small-error curve for C2H; small differences for HCN | F: Hyperfine structure can be exploited to improve curve precision, mainly for C2H | **supported**
- H: The assumed emitting layers are consistent with the assumed thermal structure | E: Derive optical depth profiles from the data and the assumed T(R,z) and z(R) | R: tau values compatible with independent estimates | F: Assumed emitting layers are suitable for curve extraction | **supported**
- H: Beam smearing biases rotation curves near emission gaps | E: Compare radial intensity gradient with velocity difference between C2H or HCN and 12CO curves | R: Strong anticorrelation with radius | F: Beam smearing causes apparent velocity deviations linked to intensity gradients, opposite in sign to pressure effects | **supported**
- H: Results are insensitive to the parameterization of the molecular emitting layers | E: Repeat the fit with flat emission and with nonparametric layers | R: Nonparametric: <~1% (M_star), <~30% (M_d), <~13% (R_c); flat: up to 10%, 18%, 20% | F: Main results are robust, with disk mass most affected | **partially**

## Reasoning

- Why this data: Very bright HD 163296 disk with exquisite-quality multi-molecule MAPS data  
  > "We focused on the very bright disk of HD 163296 and selected exquisite quality multi-molecule data from the Molecules with ALMA at Planet-forming Scales (MAPS) Large Program" (1 Introduction)
- Why this method: Fit all rotation curves with a thermally stratified model to account for vertical temperature structure  
  > "we choose to simultaneously fit our seven rotation curves including the contribution from vertical thermal stratification" (3.3 Vertically stratified model)
- Alternative: Isothermal model rejected: gives R_c=48.1 au, considered too low and cannot reproduce velocity differences  
  > "a very low value for the scale radius and a clear sign that we are probably underestimating it" (4.1 Multi-molecule fit)
- Alternative: Single-Gaussian fit for hyperfine lines judged less accurate  
  > "the standard extraction methods (that fit a quadratic or Gaussian function to the spectrum) are not adequate to fit these multi-peaked spectra" (3.2.2 Multi-Gaussian methods)
- Alternative: Flat (midplane) emission tested for low-S/N lines  
  > "we computed the rotation curves of these molecules assuming flat emission (i.e., originating at the disk midplane)" (3.2 Rotation curves extraction)
- How they decided it was enough: Added molecules one at a time and tracked reduced chi2 and parameter changes  
  > "we fitted the rotation curves starting with two molecules and then progressively adding one molecule at a time" (4.1 Multi-molecule fit)
- Limitation (authors): Rotation-curve uncertainties are statistical only and underestimated, so parameter errors are underestimated  
  > "this is an underestimate as we are taking into account only the statistical errors on the values, but no systematic errors" (4.1 Multi-molecule fit)
- Limitation (authors): Temperature-structure uncertainties not propagated  
  > "In this work we did not account for the uncertainties in the temperature structure of the disk." (4.1 Multi-molecule fit)
- Limitation (authors): Model lacks pressure substructure, so oscillations in velocity differences are not recovered  
  > "As we are not accounting for pressure modulated substructures in our model, we are not able to recover the oscillating behavior of the measured velocity difference." (4.1 Multi-molecule fit)
- Limitation (authors): eddy ignores back-side emission contamination and assumes axisymmetry  
  > "an important contamination from the back side of the disks can complicate the spectra alignment and so the goodness of the fit" (3.2.1 Limitations of the method)
- Limitation (authors): Rotation curve extraction unreliable around R~150 au for H2CO due to low S/N  
  > "the signal-to-noise ratio is too low to allow an efficient extraction of the rotation velocity" (4.1 Multi-molecule fit)
- Caveat (inferred, ours): Formal parameter uncertainties (1e-4 level) are not credible; real errors are dominated by systematics (emitting layers, temperature, geometry)
- Caveat (inferred, ours): Temperature structure and emitting layers are inputs from other papers, so results are conditional on them
- Caveat (inferred, ours): Seven curves fit with a single parametric model with gamma fixed at 1; no priors reported
- Caveat (inferred, ours): Beam smearing affects HCN and C2H curves but is not modelled in the fit

## Reproducibility

- Data public (paper): MAPS Large Program data are publicly available  
  > "the publicly available high spatial and spectral resolution data provided by the MAPS ALMA Large Program" (2.2 Targeted emission lines)
- Products in archive: Radial intensity profiles in the MAPS database (alma-maps.info)  
  > "Radial intensity profiles are available in the MAPS database at" (Footnote 1)
- Code: DySc is public on GitHub (github.com/crislong/DySc)  
  > "The code is publicly available at" (Footnote 2)
- Missing: Exact MAPS cube versions and processing options
- Missing: Priors and initial conditions of the DySc fit
- Missing: eddy version with the new multi-Gaussian routine and annulus/radial-range settings
- Missing: Distance and systemic velocity
- Data volume (inferred): Seven MAPS image cubes (roughly tens of GB); much less if using the MAPS-distributed products
- Score (inferred): 3/5, Public data and public fitting code with a tabulated numeric result, but the MAPS products, eddy settings, radial ranges and fit priors are not given, and the modified eddy is not stated as released.
- Rediscovery candidate: yes, MAPS data are public, DySc is public, the model and emcee setup are described, and the main results are numeric (M_star, M_d, R_c), though eddy settings must be inferred.

## Links

- Method: (cite: teague_eddy) (eddy rotation curve extraction package)
- Method: (cite: martire) (Stratified rotation-curve model and prior two-molecule fit)
- Method: (cite: maps4) (2D thermal structure of the disk)
- Method: (cite: paneque) (Molecular emitting layers)
- Method: (cite: dullemond2020) (Parametric T(R,z) law)
- Companion: (cite: maps1) (MAPS Large Program overview and source of the data and disk geometry)
- Companion: (cite: maps5) (Isothermal H/R and q, and R_c comparison)
- Related: MAPS ALMA Large Program (2018.1.01055.L)

## Checks

```json
{
 "quotes": 108,
 "quotes_ok": 108,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 116,
  "stated": 72,
  "rate": 0.621
 },
 "evidence_ok": true
}
```
