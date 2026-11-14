# exoALMA. XII. Weighing and Sizing exoALMA Disks with Rotation Curve Modelling

`2025ApJ...984L..17L` | The Astrophysical Journal Letters 2025 | first author: Longarini, Cristiano | arXiv: 2504.18726 | DOI: 10.3847/2041-8213/adc431

Card schema 1.0 | model gpt-6.1-sol | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: Constrain stellar masses, disk masses and density scale radii from rotation curves, then investigate gas-to-dust ratios, gravitational stability and angular momentum transport.  
  > "we constrain the stellar mass, the disk mass and the density scale radius through precise characterization of the pressure gradient and disk self gravity." (Abstract); "We evaluated the Toomre parameter to assess gravitational stability and found that all sources are gravitationally stable, consistent with the absence of prominent spiral structures." (Conclusions); "We use the fiducial values for the disk masses to compute the gas-to-dust ratio, employing the dust masses obtained by (cite: Curone_exoALMA)." (Gas to dust ratio)
- Target **AA Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **DM Tau**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **HD 34282**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1615**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1842**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **J1852**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **LkCa15**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **PDS66**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **SY Cha**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **V4046 Sgr**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01123.L
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
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Line: 13CO J=3-2 (not stated)
- External data: DISCMINER rotation curves extracted using the default cubes.  
  > "The rotation curves used in this work have been extracted with DISCMINER and thoroughly discussed in (cite: Stadler_exoALMA) using the default cubes." (Rotation curve fits) [from (cite: Stadler_exoALMA)]
- External data: Emitting-layer heights and geometrical parameters used in the fits; Table 4.  
  > "The heights of the emitting layers have been obtained with DISCMINER (cite: Izquierdo_exoALMA) and the thermal parameters with DISKSURF (cite: Galloway_exoALMA)." (Geometrical and thermal parameters of the sources); "Tables [4](#tab:discminer_parameters) and [5](#tab:temperature_profiles) show the emitting layer and the thermal parameters used for the fitting procedure, respectively." (Geometrical and thermal parameters of the sources) [from (cite: Izquierdo_exoALMA)]
- External data: Dartois thermal-structure best fits, Table 5, and thermal-parameter posterior distributions.  
  > "In this work, we will use the Dartois prescription with the best fit values for the thermal parameters obtained by (cite: Galloway_exoALMA)" (2D temperature structure); "To incorporate the systematic, we decided to run each EMCEE fit 100 times, drawing the thermal parameters from the posterior distribution of (cite: Galloway_exoALMA)." (Systematic uncertainties) [from (cite: Galloway_exoALMA)]
- External data: DISCMINER stellar masses for comparison with dynamical stellar masses.  
  > "The dynamical stellar masses generally deviate from the best fit values provided by DISCMINER (cite: Teague_exoALMA; Izquierdo_exoALMA)." (Stellar masses) [from (cite: Teague_exoALMA; Izquierdo_exoALMA)]
- External data: Dust masses and dust flux-based radii.  
  > "We use the fiducial values for the disk masses to compute the gas-to-dust ratio, employing the dust masses obtained by (cite: Curone_exoALMA)." (Gas to dust ratio); "the radii enclosing the 68% of the $^{12}$CO, $^{13}$CO (cite: Galloway_exoALMA) and dust emission (cite: Curone_exoALMA)" (Scale radii) [from (cite: Curone_exoALMA)]
- External data: CO flux-based radii.  
  > "the radii enclosing the 68% of the $^{12}$CO, $^{13}$CO (cite: Galloway_exoALMA) and dust emission (cite: Curone_exoALMA)" (Scale radii) [from (cite: Galloway_exoALMA)]
- External data: MAPS source masses and scale radii.  
  > "The masses and scale radii of the MAPS sources are taken from (cite: martire24), and the flux based radii from (cite: MAPSIV)." (Scale radii) [from (cite: martire24)]
- External data: MAPS flux-based radii.  
  > "The masses and scale radii of the MAPS sources are taken from (cite: martire24), and the flux based radii from (cite: MAPSIV)." (Scale radii) [from (cite: MAPSIV)]
- External data: CO abundances used to recompute theoretical CO radii.  
  > "The grey crosses in Fig. [5](#radii_comparison_plot) represent the values of $R_{\rm CO}$ calculated using the CO abundance derived by (cite: Trapman_exoALMA)." (Gas based measurement) [from (cite: Trapman_exoALMA)]
- External data: CO-depletion inference used for comparison; not entirely independent of the dynamical masses.  
  > "(cite: Rosotti_exoALMA) derived the CO depletion required to reconcile their estimated disk masses with the dynamical values presented in this paper, meaning their method is not entirely independent of our estimates." (Gas based measurement) [from (cite: Rosotti_exoALMA)]
- External data: AA Tau and SY Cha stellar accretion rates; adopted individual accretion-rate uncertainty of 0.35 dex.  
  > "**AA Tau** | $-7.35 \pm 0.35$ | (cite: manara23)" (Table 3); "**SY Cha** | $-9.89 \pm 0.35$ | (cite: manara23)" (Table 3); "As reported by (cite: manara23), the fractional uncertainty in individual accretion rate measurements at any given time is approximately 0.35 dex, a value which we have adopted for our analysis." (Transport of angular momentum - effective $\alpha_S$) [from (cite: manara23)]
- External data: Stellar accretion rates used in Table 3.  
  > "**DM Tau** | $-8.2 \pm 0.35$ | (cite: manara14)" (Table 3); "**J1615** | $-8.25 \pm 0.35$ | (cite: manara14)" (Table 3); "**LkCa15** | $-8.7 \pm 0.35$ | (cite: manara14)" (Table 3) [from (cite: manara14)]
- External data: HD 34282 stellar accretion rate.  
  > "**HD 34282** | $-7.69 \pm 0.35$ | (cite: fairlamb15)" (Table 3) [from (cite: fairlamb15)]
- External data: PDS66 stellar accretion rate.  
  > "**PDS66** | $-9.18 \pm 0.35$ | (cite: ingleby13)" (Table 3) [from (cite: ingleby13)]
- External data: V4046 Sgr stellar accretion rate.  
  > "**V4046 Sgr** | $-9.3 \pm 0.35$ | (cite: donati11)" (Table 3) [from (cite: donati11)]
- External data: MAPS stellar accretion rates.  
  > "**AS 209** | $-7.3 \pm 0.35$ | (cite: oberg21)" (Table 3); "**GM Aur** | $-8.1 \pm 0.35$ | (cite: oberg21)" (Table 3); "**MWC 480** | $-6.9 \pm 0.35$ | (cite: oberg21)" (Table 3) [from (cite: oberg21)]
- External data: DM Tau HD-based disk-mass measurement.  
  > "Its mass was estimated from observation of hydrogen deuteride HD by (cite: mcclure16)." (Disk masses) [from (cite: mcclure16)]
- External data: DM Tau N2H+ and HD-based disk-mass measurements.  
  > "The value we obtained in our study is consistent with both N$_2$H$^+$ and HD based measurements of (cite: trapman22)." (Disk masses) [from (cite: trapman22)]
- External data: HD 34282 CO-isotopologue gas-mass estimate.  
  > "(cite: stapper24) constrained gas masses of Herbig disks using CO isotopologues, and HD 34282 is within their sample." (Disk masses) [from (cite: stapper24)]
- External data: LkCa15 radiative-transfer disk-mass estimate.  
  > "(cite: jin19) constrain gas and dust distribution in the LkCa15 disk by comparing radiative transfer models with the $^{12}$CO and dust emission from ALMA." (Disk masses) [from (cite: jin19)]
- External data: LkCa15 thermochemical gas-mass estimate.  
  > "Conversely, (cite: sturm23) measured LkCa15 gas mass using CO, $^{13}$CO, C$^{18}$O and C$^{17}$O lines and modeling them with thermochemical models." (Disk masses) [from (cite: sturm23)]
- External data: PDS66 CO-isotopologue disk-mass estimate.  
  > "(cite: ribas23) estimated the disk mass of PDS 66 comparing the CO isotopologues’ fluxes with models of (cite: williams14) and (cite: miotello16)" (Disk masses) [from (cite: ribas23)]
- External data: V4046 Sgr CO-isotopologue disk-mass estimate.  
  > "(cite: miotello16) presented chemical models to infer the disk mass from CO isotopologues emission." (Disk masses); "In that work, they gave an estimate of V4046 Sgr disk mass being $\sim10^{-3}\rm M_\odot$." (Disk masses) [from (cite: miotello16)]
- External data: V4046 Sgr spectroscopic-binary period and mass ratio.  
  > "V4046 Sgr is a known spectroscopic binary with a period of 2.4 days and a mass ratio $q\simeq0.94$ (cite: stempels04)." (Disk masses) [from (cite: stempels04)]
- External data: Independent angular momentum transport constraints from molecular line broadening.  
  > "**DM Tau** | $-8.2 \pm 0.35$ | (cite: manara14) | $2.19^{+2.72}_{-1.21}\times10^{-3}$ | $0.08 \pm 0.02$ | (cite: flaherty20)" (Table 3); "**HD 163296** | $-7.4 \pm 0.35$ | (cite: oberg21) | $4.31^{+5.35}_{-2.38}\times10^{-3}$ | $<0.003$ | (cite: flaherty15; flaherty17)" (Table 3) [from (cite: flaherty15; flaherty17; flaherty20)]
- External data: IM Lup angular momentum transport constraint from dust emission modelling.  
  > "Finally, for IM Lup (cite: franceschi23) modeled dust emission with different $\alpha_S$ values, post-processed the models with radiative transfer codes and compared with the actual data." (Transport of angular momentum - effective $\alpha_S$) [from (cite: franceschi23)]
- External data: IM Lup turbulence constraint from CN and C2H.  
  > "By contrast, (cite: paneque23) estimate the viscosity through the characterization of CN and C$_2$H." (Transport of angular momentum - effective $\alpha_S$); "Leveraging on the optical depth properties of these two tracers, they measured the turbulence from the non-thermal broadening of the line, at the location of the emitting layer." (Transport of angular momentum - effective $\alpha_S$) [from (cite: paneque23)]
- External data: IM Lup molecular-line-broadening angular momentum transport constraint.  
  > "Recently, also (cite: flaherty24) estimated the $\alpha$ for IM Lup by molecular line broadening model, showing a good agreement with (cite: paneque23)." (Transport of angular momentum - effective $\alpha_S$) [from (cite: flaherty24)]
- Simulation/model as data: Thermochemical relation between CO 90%-flux radius, scale radius and disk mass from (cite: toci23; trapman23).  
  > "This issue was addressed by (cite: toci23; trapman23), who found a relationship between $R_{12\rm CO}^{90}$ and $R_c$ and $M_d$" (Gas based measurement); "(cite: trapman23) obtain Eq. [\[trap_rad\]](#trap_rad) using thermochemical models, fixing the CO abundance at $X_{\rm CO}=10^{-4}$." (Gas based measurement)
- Simulation/model as data: Viscosity, grain-growth and radial-drift disk-evolution models from (cite: toci21).  
  > "(cite: toci21) presented theoretical models of protoplanetary disk evolution influenced by viscosity, grain growth, and radial drift, and studied the ratio between the scale radius and the dust." (Dust based measurement)

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

- Rotation-curve model including thermal stratification.  
  > "The model we adopt to describe the rotation curve of a protoplanetary disk is the one presented in (cite: Lodato23), then generalized by (cite: martire24) including the disk thermal stratification." (Physical model) [from (cite: Lodato23; martire24)]
- Self-similar surface-density solution.  
  > "Although the calculations are valid for an arbitrary surface density $\Sigma$, in this work we assume that it is described by the self-similar solution of (cite: Lyndenbell74)" (Model for the rotation curve) [from (cite: Lyndenbell74)]
- Dartois temperature prescription and best-fit thermal parameters.  
  > "(cite: Galloway_exoALMA) obtained the 2D thermal structures of exoALMA disks from $^{12}$CO and $^{13}$CO datacubes, adopting the Dartois (cite: Dartois03) prescription" (2D temperature structure); "In this work, we will use the Dartois prescription with the best fit values for the thermal parameters obtained by (cite: Galloway_exoALMA)" (2D temperature structure) [from (cite: Dartois03); (cite: Galloway_exoALMA)]
- DISCMINER rotation curves from the default cubes and exclusion of the first two major beam sizes in radius.  
  > "The rotation curves used in this work have been extracted with DISCMINER and thoroughly discussed in (cite: Stadler_exoALMA) using the default cubes." (Rotation curve fits); "In our analysis we excluded the first two major beam sizes in radius, as discussed in (cite: Stadler_exoALMA)." (Rotation curve fits) [from (cite: Stadler_exoALMA)]
- DISCMINER emitting-layer geometry.  
  > "The heights of the emitting layers have been obtained with DISCMINER (cite: Izquierdo_exoALMA) and the thermal parameters with DISKSURF (cite: Galloway_exoALMA)." (Geometrical and thermal parameters of the sources) [from (cite: Izquierdo_exoALMA)]
- Gas-image centering procedure.  
  > "for more information on how the center of the images is found we refer to (cite: Izquierdo_exoALMA) for the gas and (cite: Curone_exoALMA) for the continuum." (Systematic uncertainties) [from (cite: Izquierdo_exoALMA)]
- Continuum-image centering procedure and dust-substructure characterization.  
  > "for more information on how the center of the images is found we refer to (cite: Izquierdo_exoALMA) for the gas and (cite: Curone_exoALMA) for the continuum." (Systematic uncertainties); "for a detailed characterization of dust substructures, we refer to (cite: Curone_exoALMA)." (Dust based measurement) [from (cite: Curone_exoALMA)]
- Linear dependence of the Lambert-function argument on CO abundance.  
  > "Assuming a linear relationship between the CO abundance and the argument of the Lambert function in Eq. [\[trap_rad\]](#trap_rad), as done in (cite: toci23)" (Gas based measurement) [from (cite: toci23)]
- AS 209 disk-mass upper limit of 0.05 times the stellar mass for the effective-alpha calculation.  
  > "for AS 209 we use $M_d=0.05M_\star$ as an upper limit, as commented in (cite: martire24)." (Transport of angular momentum - effective $\alpha_S$) [from (cite: martire24)]
- Accretion-rate uncertainty of 0.35 dex.  
  > "As reported by (cite: manara23), the fractional uncertainty in individual accretion rate measurements at any given time is approximately 0.35 dex, a value which we have adopted for our analysis." (Transport of angular momentum - effective $\alpha_S$) [from (cite: manara23)]
- Effective-alpha relation within a self-similar evolution framework.  
  > "By measuring the accretion rates, we can in principle constrain the instantaneous $\alpha_S$ using (i.e. (cite: hartmann98))" (Transport of angular momentum - effective $\alpha_S$) [from (cite: hartmann98)]

### Not stated but needed to reproduce (our reading)

- Exact default-cube files, calibration history, imaging settings, beam sizes and spectral sampling.
- Machine-readable rotation curves, velocity uncertainties, radial sampling and full radial masks for each isotopologue.
- Target distances used to convert angular measurements to au.
- Explicit emitting-height function associated with the Table 4 parameters.
- Thermal-parameter posterior samples, including their joint covariance, and the treatment of Table 5 Z0 in arcsec.
- How the 100 thermal-realization posteriors are combined into the final estimates and asymmetric intervals.
- Posterior point-estimate convention, interval probability, convergence criteria and random seeds.
- Explicit adopted mean molecular weight; the text only describes 2.35 as usually assumed.
- Exact numerical integration and differentiation settings for the stratified rotation model.
- Dust-mass opacity and temperature assumptions inherited through the continuum analysis.
- Source-by-source 90%-flux CO radii and CO-depletion factors used for the thermochemical comparison.

## Analysis recipe

1. **Assemble rotation curves and disk structures**: Use DISCMINER rotation curves and emitting layers, with DISKSURF thermal structures; adopt the tabulated geometrical and thermal parameters.  
  > "The rotation curves used in this work have been extracted with DISCMINER and thoroughly discussed in (cite: Stadler_exoALMA) using the default cubes." (Rotation curve fits); "The emitting layers of $^{12}$CO and $^{13}$CO are an output of DISCMINER as well." (Rotation curve fits); "Finally the thermal structure are extracted with DISKSURF and thoroughly discussed in (cite: Galloway_exoALMA)." (Rotation curve fits)
   - software: DISCMINER, DISKSURF
   - parameter: Emitting-layer and thermal parameters in Tables 4 and 5.  
  > "Tables [4](#tab:discminer_parameters) and [5](#tab:temperature_profiles) show the emitting layer and the thermal parameters used for the fitting procedure, respectively." (Geometrical and thermal parameters of the sources)
   - assumption: Dartois prescription with inherited best-fit thermal parameters.  
  > "In this work, we will use the Dartois prescription with the best fit values for the thermal parameters obtained by (cite: Galloway_exoALMA)" (2D temperature structure)
   - fitting: _not stated_
   - validation: _not stated_
2. **Select sources and usable radial regions**: Require well-defined CO surfaces and no strong non-axisymmetric features; exclude the first two major beam sizes, truncate AA Tau 12CO at 250 au and exclude AA Tau from statistical analyses.  
  > "We discarded sources that show strong non-axisymmetric features (MWC 758, CQ Tau) and low inclination ones (HD 135344B, HD 143006, J1604), for which the extraction of the emitting layer is not well defined." (Sample); "In our analysis we excluded the first two major beam sizes in radius, as discussed in (cite: Stadler_exoALMA)." (Rotation curve fits); "Consequently, for the statistical analysis in this paper, we exclude AA Tau from the sample" (Rotation curve fits)
   - parameter: AA Tau 12CO outer fitting radius: 250 au.  
  > "When fitting AA Tau, we limited our analysis out to 250au for the $^{12}$CO" (Rotation curve fits)
   - assumption: Azimuthal averaging and centrifugal balance.  
  > "the absence of non-axisymmetric features, which may affect the azimuthal averaging, intrinsic to the definition of rotation curve, and the very assumption of centrifugal balance." (Sample)
   - fitting: _not stated_
   - validation: Include and exclude diffuse-backside regions in SY Cha and LkCa15; results remain consistent.  
  > "The issue of the diffuse backside is also observed in SY Cha at $R>400$ au and in the $^{13}$CO data of LkCa15 (cite: Galloway_exoALMA)." (Rotation curve fits); "We tested the robustness of the fits by including and excluding these regions, demonstrating that the results remain consistent for these disks." (Rotation curve fits)
3. **Fit stellar mass, disk mass and scale radius**: Simultaneously fit 12CO and 13CO rotation curves with the thermally stratified model including stellar gravity, pressure gradient and disk self-gravity.  
  > "For each disk, both the $^{12}$CO and $^{13}$CO rotation curves are fitted simultaneously." (Rotation curve fits); "The model we adopt to describe the rotation curve of a protoplanetary disk is the one presented in (cite: Lodato23), then generalized by (cite: martire24) including the disk thermal stratification." (Physical model); "we constrain the stellar mass, the disk mass and the density scale radius through precise characterization of the pressure gradient and disk self gravity." (Abstract)
   - software: DYSC, EMCEE
   - parameter: 10 walkers; 5000 burnin steps; 5000 steps; walkers initially uniform within prior intervals.  
  > "All the DYSC fits were performed using $10$ walkers, $5000$ steps of burnin and $5000$ steps." (Rotation curve fits); "Initially, the walkers are uniformly distributed within their prior intervals." (Rotation curve fits)
   - assumption: Self-similar surface density with gamma=1.  
  > "in this work we assume that it is described by the self-similar solution of (cite: Lyndenbell74)" (Model for the rotation curve); "All the fits are performed fixing the power law coefficient of the surface density $\gamma=1$, underestimating the true uncertainties." (DySc Code and statistical framework)
   - assumption: Gaussian, uncorrelated velocity measurements with standard deviation sigma_v.  
  > "Here, we make the standard assumption that the data are distributed around the true value following a Gaussian distribution, with standard deviation $\sigma_v$, and that they are not correlated." (DySc Code and statistical framework)
   - fitting: EMCEE MCMC; Gaussian likelihood; uniform priors M_star=[0,5] M_sun, M_d=[0,1] M_sun and R_c=[10,1000] au.  
  > "The code implements Markov-Chain-Monte-Carlo through the EMCEE library (cite: emcee)." (DySc Code and statistical framework); "Here, we make the standard assumption that the data are distributed around the true value following a Gaussian distribution, with standard deviation $\sigma_v$, and that they are not correlated." (DySc Code and statistical framework); "The chosen priors for the model parameters are uniform distributions respectively centred on $M_\star \in \mathcal{U} [0,5]\text{M}_\odot$, $M_d \in \mathcal{U}  [0,1]\text{M}_\odot$ and $R_c \in \mathcal{U}  [10, 1000]\text{au}$" (DySc Code and statistical framework)
   - validation: Inspect best-fit rotation curves, residuals and posterior corner plots; test Gaussian gaps and rings on LkCa15.  
  > "Figures [8](#rcurves1), [9](#rcurves2) and [10](#rcurves3) show the best fit rotation curves with the model residuals." (Best fit models and corner plots); "Figures [11](#c1), [12](#c3) and [13](#c5) show the corner plots and the posterior distributions for stellar mass, disc mass and scale radius." (Best fit models and corner plots); "We applied this approach to the rotation curve of a reference disc, LkCa 15, fitting the data both with and without the inclusion of substructures." (Model for the rotation curve)
4. **Propagate thermal-structure uncertainty**: Repeat each EMCEE fit 100 times with thermal parameters drawn from the inherited posterior distribution; report dynamical parameters and uncertainties.  
  > "To incorporate the systematic, we decided to run each EMCEE fit 100 times, drawing the thermal parameters from the posterior distribution of (cite: Galloway_exoALMA)." (Systematic uncertainties); "This procedure allows us to take into account the systematic errors driven by the thermal structure, returning a realistic uncertainty for the best fit parameters, listed in table [1](#table_results)." (Systematic uncertainties)
   - software: DYSC, EMCEE
   - parameter: 100 fits per disk.  
  > "To incorporate the systematic, we decided to run each EMCEE fit 100 times, drawing the thermal parameters from the posterior distribution of (cite: Galloway_exoALMA)." (Systematic uncertainties)
   - assumption: Thermal structure dominates systematic uncertainties.  
  > "However, the thermal structure dominates the systematic uncertainties, since it directly impacts the pressure gradient characterization." (Systematic uncertainties)
   - fitting: Repeat the EMCEE fitting procedure with draws from the thermal posterior.  
  > "To incorporate the systematic, we decided to run each EMCEE fit 100 times, drawing the thermal parameters from the posterior distribution of (cite: Galloway_exoALMA)." (Systematic uncertainties)
   - validation: Compare disk masses against independent literature measurements.  
  > "In Figure [2](#comparison_masses_plot), we compare the dynamical disk mass estimated in this paper to these independently estimates." (Disk masses)
5. **Calculate mass ratios**: Calculate disk-to-star and gas-to-dust ratios from the dynamical masses and inherited dust masses; propagate posterior distributions; exclude AA Tau from the average gas-to-dust ratio.  
  > "We use the fiducial values for the disk masses to compute the gas-to-dust ratio, employing the dust masses obtained by (cite: Curone_exoALMA)." (Gas to dust ratio); "The errors on the disk to star mass ratio and on the gas to dust ratio have been computed using the posterior distributions for the relevant quantities." (Table 1); "To compute the average gas-to-dust ratio, we have excluded AA Tau." (Gas to dust ratio)
   - assumption: Optically thin continuum emission for the inherited dust masses.  
  > "We compared the dynamical disk masses with the dust based ones (cite: Curone_exoALMA), with the assumption of optically thin continuum emission, to determine the gas to dust ratio." (Conclusions)
   - fitting: _not stated_
   - validation: _not stated_
6. **Assess gravitational stability**: Compute surface-density and Toomre-Q profiles from the fitted disk structure and midplane temperature; exclude AA Tau.  
  > "To investigate the likelihood of a disk to be gravitationally unstable, we compute the Toomre Q parameter" (Gravitational instability?); "Figure [4](#ToomreQ_plot) shows the surface density profiles and the Toomre parameter profiles for the disks within our sample." (Gravitational instability?); "We are excluding AA Tau because of the large uncertainties" (Gravitational instability?)
   - assumption: Midplane temperature extrapolated from inherited 2D thermal structures.  
  > "We underline that the temperature at the midplane is extrapolated from the 2D thermal structures (cite: Galloway_exoALMA)." (Gravitational instability?)
   - assumption: Instability onset at Q approximately 1 under the WKB quadratic dispersion relation.  
  > "According to the WKB (Wentzel–Kramers–Brillouin) quadratic dispersion relation (cite: linshu64; toomre64), the onset of the instability occur when $Q \sim 1$." (Gravitational instability?)
   - fitting: _not stated_
   - validation: Stability is consistent with the absence of prominent spiral structures.  
  > "We evaluated the Toomre parameter to assess gravitational stability and found that all sources are gravitationally stable, consistent with the absence of prominent spiral structures." (Conclusions)
7. **Compare dynamical and emission radii**: Compare R_c with 68%-flux gas and dust radii; predict 90%-flux 12CO radii from M_d and R_c; recompute with inherited CO depletion.  
  > "the radii enclosing the 68% of the $^{12}$CO, $^{13}$CO (cite: Galloway_exoALMA) and dust emission (cite: Curone_exoALMA), and the scale radii $R_c$ we find by modeling the rotation curve." (Scale radii); "Figure [6](#trapman_radii) shows the comparison between the radius enclosing the 90% of the $^{12}$CO emission and the theoretical expectation according to Eq. [\[trap_rad\]](#trap_rad)." (Gas based measurement); "We recomputed the CO radii using the CO depletion factor derived by (cite: Trapman_exoALMA) through forward-modeling N$_2$H$^+$ and C$^{18}$O emissions." (Conclusions)
   - parameter: 68%-flux radii for gas/dust comparison; 90%-flux 12CO radii for thermochemical comparison.  
  > "the radii enclosing the 68% of the $^{12}$CO, $^{13}$CO (cite: Galloway_exoALMA) and dust emission (cite: Curone_exoALMA)" (Scale radii); "Figure [6](#trapman_radii) shows the comparison between the radius enclosing the 90% of the $^{12}$CO emission and the theoretical expectation according to Eq. [\[trap_rad\]](#trap_rad)." (Gas based measurement)
   - assumption: Initial thermochemical relation assumes X_CO=10^-4.  
  > "(cite: trapman23) obtain Eq. [\[trap_rad\]](#trap_rad) using thermochemical models, fixing the CO abundance at $X_{\rm CO}=10^{-4}$." (Gas based measurement)
   - assumption: CO abundance scales linearly with the Lambert-function argument.  
  > "Assuming a linear relationship between the CO abundance and the argument of the Lambert function in Eq. [\[trap_rad\]](#trap_rad), as done in (cite: toci23)" (Gas based measurement)
   - fitting: _not stated_
   - validation: Propagate disk-mass and scale-radius uncertainties; compare predictions with observed CO radii.  
  > "The error bars take into account the uncertainty on the disk mass and scale radius." (Gas based measurement); "For most of the sources, using these CO abundances result in a better agreement with the observed values." (Gas based measurement)
8. **Infer effective angular momentum transport**: Calculate alpha_S=(2/3)[Mdot_star/(M_d Omega_c)](H_c/R_c)^-2 using fitted disk properties and literature accretion rates, evaluated at R_c.  
  > "\alpha_S = \frac{2}{3} \frac{\dot{M}_\star}{M_d\Omega_c}\left(\frac{H_{c}}{R_{c}}\right)^{-2}," (Transport of angular momentum - effective $\alpha_S$); "where the subscript $c$ denotes that the corresponding quantity is evaluated at the scale radius." (Transport of angular momentum - effective $\alpha_S$)
   - parameter: Adopt 0.35 dex uncertainty in individual accretion rates.  
  > "As reported by (cite: manara23), the fractional uncertainty in individual accretion rate measurements at any given time is approximately 0.35 dex, a value which we have adopted for our analysis." (Transport of angular momentum - effective $\alpha_S$)
   - parameter: AS 209: use M_d=0.05 M_star as an upper limit.  
  > "for AS 209 we use $M_d=0.05M_\star$ as an upper limit, as commented in (cite: martire24)." (Transport of angular momentum - effective $\alpha_S$)
   - assumption: Self-similar surface-density evolution.  
  > "assuming self-similar evolution of the surface density, we constrain the effective $\alpha_S$ for these systems." (Abstract)
   - assumption: Stellar accretion at less than 1 au equals disk accretion at the scale radius.  
  > "We point out that here we are assuming that stellar accretion, which happens in the $<1$au region of the disk is equal to the disk accretion, measured at the scale radius." (Transport of angular momentum - effective $\alpha_S$)
   - assumption: Interpret alpha_S as effective angular momentum transport efficiency, without requiring turbulence.  
  > "Additionally, the formula does not imply that accretion is driven by turbulence; the values it returns should be interpreted as an effective $\alpha_S$, i.e. the amount of transported angular momentum." (Transport of angular momentum - effective $\alpha_S$)
   - fitting: _not stated_
   - validation: Compare with independent line-broadening and dust-profile constraints.  
  > "there are independent $\alpha_S$ constraints, obtained by modeling the non-thermal molecular line broadening (cite: flaherty15; flaherty17; flaherty20) or by determining the dust emission radial profile with radiative transfer models (cite: franceschi23)." (Transport of angular momentum - effective $\alpha_S$)

## Software

- **DISCMINER** : Extract rotation curves and emitting layers; provide comparison stellar masses.  
  > "The rotation curves used in this work have been extracted with DISCMINER and thoroughly discussed in (cite: Stadler_exoALMA) using the default cubes." (Rotation curve fits); "The emitting layers of $^{12}$CO and $^{13}$CO are an output of DISCMINER as well." (Rotation curve fits); "The dynamical stellar masses generally deviate from the best fit values provided by DISCMINER (cite: Teague_exoALMA; Izquierdo_exoALMA)." (Stellar masses)
- **DISKSURF** : Extract thermal structures and non-parametric emitting surfaces.  
  > "Finally the thermal structure are extracted with DISKSURF and thoroughly discussed in (cite: Galloway_exoALMA)." (Rotation curve fits); "As a result, the non-parametric emitting surface extracted by DISKSURF differs from the parametric one used by DISCMINER." (The case of AA Tau)
- **DYSC** : Fit stellar mass, disk mass and scale radius using the stratified rotation-curve model.  
  > "We implemented the fitting procedure for stellar mass, disk mass and scale radius based on the model of Eq. [\[rotationcurve_strat\]](#rotationcurve_strat) in the code DYSC" (DySc Code and statistical framework)
- **EMCEE** : Markov-Chain-Monte-Carlo fitting within DYSC.  
  > "The code implements Markov-Chain-Monte-Carlo through the EMCEE library (cite: emcee)." (DySc Code and statistical framework)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AA Tau stellar mass | 0.624 | +0.033/-0.035 | M_\odot | 4 | **AA Tau** / $0.624^{+0.033}_{-0.035}$ / $0.155^{+0.036}_{-0.036}$ / $156^{+106}_{-41}$ |
| AA Tau disk mass | 0.155 | +0.036/-0.036 | M_\odot | 4 | **AA Tau** / $0.624^{+0.033}_{-0.035}$ / $0.155^{+0.036}_{-0.036}$ / $156^{+106}_{-41}$ |
| AA Tau scale radius | 156 | +106/-41 | au | 4 | **AA Tau** / $0.624^{+0.033}_{-0.035}$ / $0.155^{+0.036}_{-0.036}$ / $156^{+106}_{-41}$ |
| DM Tau stellar mass | 0.468 | +0.014/-0.015 | M_\odot | 4 | **DM Tau** / $0.468^{+0.014}_{-0.015}$ / $0.057^{+0.019}_{-0.020}$ / $240^{+42}_{-27}$ |
| DM Tau disk mass | 0.057 | +0.019/-0.020 | M_\odot | 4 | **DM Tau** / $0.468^{+0.014}_{-0.015}$ / $0.057^{+0.019}_{-0.020}$ / $240^{+42}_{-27}$ |
| DM Tau scale radius | 240 | +42/-27 | au | 4 | **DM Tau** / $0.468^{+0.014}_{-0.015}$ / $0.057^{+0.019}_{-0.020}$ / $240^{+42}_{-27}$ |
| HD 34282 stellar mass | 1.520 | +0.025/-0.031 | M_\odot | 4 | **HD 34282** / $1.520^{+0.025}_{-0.031}$ / $0.143^{+0.045}_{-0.041}$ / $370^{+109}_{-78}$ |
| HD 34282 disk mass | 0.143 | +0.045/-0.041 | M_\odot | 4 | **HD 34282** / $1.520^{+0.025}_{-0.031}$ / $0.143^{+0.045}_{-0.041}$ / $370^{+109}_{-78}$ |
| HD 34282 scale radius | 370 | +109/-78 | au | 4 | **HD 34282** / $1.520^{+0.025}_{-0.031}$ / $0.143^{+0.045}_{-0.041}$ / $370^{+109}_{-78}$ |
| J1615 stellar mass | 1.105 | +0.011/-0.012 | M_\odot | 4 | **J1615** / $1.105^{+0.011}_{-0.012}$ / $0.082^{+0.014}_{-0.014}$ / $167^{+20}_{-15}$ |
| J1615 disk mass | 0.082 | +0.014/-0.014 | M_\odot | 4 | **J1615** / $1.105^{+0.011}_{-0.012}$ / $0.082^{+0.014}_{-0.014}$ / $167^{+20}_{-15}$ |
| J1615 scale radius | 167 | +20/-15 | au | 4 | **J1615** / $1.105^{+0.011}_{-0.012}$ / $0.082^{+0.014}_{-0.014}$ / $167^{+20}_{-15}$ |
| J1842 stellar mass | 1.042 | +0.010/-0.011 | M_\odot | 4 | **J1842** / $1.042^{+0.010}_{-0.011}$ / $0.078^{+0.013}_{-0.014}$ / $231^{+102}_{-50}$ |
| J1842 disk mass | 0.078 | +0.013/-0.014 | M_\odot | 4 | **J1842** / $1.042^{+0.010}_{-0.011}$ / $0.078^{+0.013}_{-0.014}$ / $231^{+102}_{-50}$ |
| J1842 scale radius | 231 | +102/-50 | au | 4 | **J1842** / $1.042^{+0.010}_{-0.011}$ / $0.078^{+0.013}_{-0.014}$ / $231^{+102}_{-50}$ |
| J1852 stellar mass | 1.022 | +0.021/-0.021 | M_\odot | 4 | **J1852**$^{\dagger}$ / $1.022^{+0.021}_{-0.021}$ / $0.044^{+0.024}_{-0.032}$ / $87^{+69}_{-16}$ |
| J1852 disk mass; below measurability threshold | 0.044 | +0.024/-0.032 | M_\odot | 4 | **J1852**$^{\dagger}$ / $1.022^{+0.021}_{-0.021}$ / $0.044^{+0.024}_{-0.032}$ / $87^{+69}_{-16}$; In our sample, only three sources —J1852, PDS66, and V4046— have best-fit disk mass values below this threshold. |
| J1852 scale radius | 87 | +69/-16 | au | 4 | **J1852**$^{\dagger}$ / $1.022^{+0.021}_{-0.021}$ / $0.044^{+0.024}_{-0.032}$ / $87^{+69}_{-16}$ |
| LkCa15 stellar mass | 1.118 | +0.013/-0.015 | M_\odot | 4 | **LkCa15** / $1.118^{+0.013}_{-0.015}$ / $0.108^{+0.016}_{-0.016}$ / $150^{+12}_{-16}$ |
| LkCa15 disk mass | 0.108 | +0.016/-0.016 | M_\odot | 4 | **LkCa15** / $1.118^{+0.013}_{-0.015}$ / $0.108^{+0.016}_{-0.016}$ / $150^{+12}_{-16}$ |
| LkCa15 scale radius | 150 | +12/-16 | au | 4 | **LkCa15** / $1.118^{+0.013}_{-0.015}$ / $0.108^{+0.016}_{-0.016}$ / $150^{+12}_{-16}$ |
| PDS66 stellar mass | 1.299 | +0.036/-0.101 | M_\odot | 4 | **PDS66**$^{\dagger}$ / $1.299^{+0.036}_{-0.101}$ / $0.038^{+0.099}_{-0.035}$ / $28^{+12}_{-5}$ |
| PDS66 disk mass; below measurability threshold | 0.038 | +0.099/-0.035 | M_\odot | 4 | **PDS66**$^{\dagger}$ / $1.299^{+0.036}_{-0.101}$ / $0.038^{+0.099}_{-0.035}$ / $28^{+12}_{-5}$; In our sample, only three sources —J1852, PDS66, and V4046— have best-fit disk mass values below this threshold. |
| PDS66 scale radius | 28 | +12/-5 | au | 4 | **PDS66**$^{\dagger}$ / $1.299^{+0.036}_{-0.101}$ / $0.038^{+0.099}_{-0.035}$ / $28^{+12}_{-5}$ |
| SY Cha stellar mass | 0.812 | +0.037/-0.041 | M_\odot | 4 | **SY Cha** / $0.812^{+0.037}_{-0.041}$ / $0.084^{+0.044}_{-0.043}$ / $112^{+21}_{-15}$ |
| SY Cha disk mass | 0.084 | +0.044/-0.043 | M_\odot | 4 | **SY Cha** / $0.812^{+0.037}_{-0.041}$ / $0.084^{+0.044}_{-0.043}$ / $112^{+21}_{-15}$ |
| SY Cha scale radius | 112 | +21/-15 | au | 4 | **SY Cha** / $0.812^{+0.037}_{-0.041}$ / $0.084^{+0.044}_{-0.043}$ / $112^{+21}_{-15}$ |
| V4046 Sgr stellar mass | 1.777 | +0.005/-0.006 | M_\odot | 4 | **V4046 Sgr**$^{\dagger}$ / $1.777^{+0.005}_{-0.006}$ / $0.058^{+0.006}_{-0.006}$ / $99^{+5}_{-5}$ |
| V4046 Sgr disk mass; below measurability threshold | 0.058 | +0.006/-0.006 | M_\odot | 4 | **V4046 Sgr**$^{\dagger}$ / $1.777^{+0.005}_{-0.006}$ / $0.058^{+0.006}_{-0.006}$ / $99^{+5}_{-5}$; In our sample, only three sources —J1852, PDS66, and V4046— have best-fit disk mass values below this threshold. |
| V4046 Sgr scale radius | 99 | +5/-5 | au | 4 | **V4046 Sgr**$^{\dagger}$ / $1.777^{+0.005}_{-0.006}$ / $0.058^{+0.006}_{-0.006}$ / $99^{+5}_{-5}$ |
| AA Tau gas-to-dust ratio | 1417 | +326/-330 | dimensionless | 5 | 0.791 / 26.7% / 0.115 / $1417^{+326}_{-330}$ |
| DM Tau gas-to-dust ratio | 367 | +131/-121 | dimensionless | 5 | 0.453 / -3.1% / 0.162 / $367^{+131}_{-121}$ |
| HD 34282 gas-to-dust ratio | 137 | +40/-43 | dimensionless | 5 | 1.620 / 6.6% / 1.091 / $137^{+40}_{-43}$ |
| J1615 gas-to-dust ratio | 279 | +49/-49 | dimensionless | 5 | 1.140 / 3.1% / 0.308 / $279^{+49}_{-49}$ |
| J1842 gas-to-dust ratio | 759 | +134/-129 | dimensionless | 5 | 1.068 / 2.5% / 0.108 / $759^{+134}_{-129}$ |
| J1852 gas-to-dust ratio | 420 | +300/-301 | dimensionless | 5 | 1.028 / 0.6% / 0.110 / $420^{+300}_{-301}$ |
| LkCa15 gas-to-dust ratio | 339 | +49/-50 | dimensionless | 5 | 1.028 / -8.0% / 0.333 / $339^{+49}_{-50}$ |
| PDS66 gas-to-dust ratio | 364 | +342/-357 | dimensionless | 5 | 1.277 / -1.7% / 0.108 / $364^{+342}_{-357}$ |
| SY Cha gas-to-dust ratio | 517 | +266/-273 | dimensionless | 5 | 0.813 / 0.1% / 0.170 / $517^{+266}_{-273}$ |
| V4046 Sgr gas-to-dust ratio | 540 | +60/-59 | dimensionless | 5 | 1.763 / -0.8% / 0.112 / $540^{+60}_{-59}$ |
| Average gas-to-dust ratio excluding AA Tau | ~400 | not stated | dimensionless | 5 | Overall, the gas-to-dust ratios are above the standard value of 100, with an average value of $\sim 400$.; To compute the average gas-to-dust ratio, we have excluded AA Tau. |
| Massive-disk Toomre Q | >1 | not stated | dimensionless | 6 | The massive disks in our sample show $Q>1$, meaning that they all are gravitationally stable. |
| Average 12CO 68%-flux radius / dynamical scale radius | 2.5 | not stated | dimensionless | 7 | As expected, the flux-based radii are larger compared to the dynamical scale radius, showing an average ratio of $2.5$ for the $^{12}$CO and $1.75$ for the $^{13}$CO. |
| Average 13CO 68%-flux radius / dynamical scale radius | 1.75 | not stated | dimensionless | 7 | As expected, the flux-based radii are larger compared to the dynamical scale radius, showing an average ratio of $2.5$ for the $^{12}$CO and $1.75$ for the $^{13}$CO. |
| Average dust 68%-flux radius / dynamical scale radius | 0.75 | not stated | dimensionless | 7 | On average, the dust radii are smaller than the scale radii, showing an average ratio of $0.75$. |
| AA Tau effective alpha_S | 6.54×10^-3 | +8.11/-3.62 ×10^-3 | dimensionless | 8 | **AA Tau** / $-7.35 \pm 0.35$ / (cite: manara23) / $6.54^{+8.11}_{-3.62}\times10^{-3}$ |
| DM Tau effective alpha_S | 2.19×10^-3 | +2.72/-1.21 ×10^-3 | dimensionless | 8 | **DM Tau** / $-8.2 \pm 0.35$ / (cite: manara14) / $2.19^{+2.72}_{-1.21}\times10^{-3}$ |
| HD 34282 effective alpha_S | 3.86×10^-3 | +4.79/-2.14 ×10^-3 | dimensionless | 8 | **HD 34282** / $-7.69 \pm 0.35$ / (cite: fairlamb15) / $3.86^{+4.79}_{-2.14}\times10^{-3}$ |
| J1615 effective alpha_S | 1.20×10^-3 | +1.48/-0.66 ×10^-3 | dimensionless | 8 | **J1615** / $-8.25 \pm 0.35$ / (cite: manara14) / $1.20^{+1.48}_{-0.66}\times10^{-3}$ |
| J1842 effective alpha_S | 4.03×10^-4 | +4.99/-2.23 ×10^-4 | dimensionless | 8 | **J1842** / $-8.8 \pm 0.35$ / (cite: manara14) / $4.03^{+4.99}_{-2.23}\times10^{-4}$ |
| J1852 effective alpha_S | 3.62×10^-4 | +4.49/-2.01 ×10^-4 | dimensionless | 8 | **J1852** / $-8.7 \pm 0.35$ / (cite: manara14) / $3.62^{+4.49}_{-2.01}\times10^{-4}$ |
| LkCa15 effective alpha_S | 1.74×10^-4 | +2.16/-0.97 ×10^-4 | dimensionless | 8 | **LkCa15** / $-8.7 \pm 0.35$ / (cite: manara14) / $1.74^{+2.16}_{-0.97}\times10^{-4}$ |
| PDS66 effective alpha_S | 8.06×10^-5 | +9.99/-4.46 ×10^-5 | dimensionless | 8 | **PDS66** / $-9.18 \pm 0.35$ / (cite: ingleby13) / $8.06^{+9.99}_{-4.46}\times10^{-5}$ |
| SY Cha effective alpha_S | 1.66×10^-5 | +2.05/-0.92 ×10^-5 | dimensionless | 8 | **SY Cha** / $-9.89 \pm 0.35$ / (cite: manara23) / $1.66^{+2.05}_{-0.92}\times10^{-5}$ |
| V4046 Sgr effective alpha_S | 1.11×10^-4 | +1.38/-0.61 ×10^-4 | dimensionless | 8 | **V4046 Sgr** / $-9.3 \pm 0.35$ / (cite: donati11) / $1.11^{+1.38}_{-0.61}\times10^{-4}$ |
| AS 209 effective alpha_S lower limit | >1.11×10^-2 | not stated | dimensionless | 8 | **AS 209** / $-7.3 \pm 0.35$ / (cite: oberg21) / $>1.11\times10^{-2}$ |
| GM Aur effective alpha_S | 9.32×10^-4 | +11.1/-5.16 ×10^-4 | dimensionless | 8 | **GM Aur** / $-8.1 \pm 0.35$ / (cite: oberg21) / $9.32^{+11.1}_{-5.16}\times10^{-4}$ |
| HD 163296 effective alpha_S | 4.31×10^-3 | +5.35/-2.38 ×10^-3 | dimensionless | 8 | **HD 163296** / $-7.4 \pm 0.35$ / (cite: oberg21) / $4.31^{+5.35}_{-2.38}\times10^{-3}$ |
| IM Lup effective alpha_S | 1.48×10^-3 | +1.18/-0.82 ×10^-3 | dimensionless | 8 | **IM Lup** / $-7.9 \pm 0.35$ / (cite: oberg21) / $1.48^{+1.18}_{-0.82}\times10^{-3}$ |
| MWC 480 effective alpha_S | 1.41×10^-2 | +1.17/-0.78 ×10^-2 | dimensionless | 8 | **MWC 480** / $-6.9 \pm 0.35$ / (cite: oberg21) / $1.41^{+1.17}_{-0.78}\times10^{-2}$ |
| Effective alpha_S range | 10^-5 to 10^-2 | not stated | dimensionless | 8 | We find a broad range of $\alpha_S$ values ranging between $10^{-5}$ and $10^{-2}$. |
| Typical stellar-mass difference from DISCMINER excluding AA Tau | ~5% | not stated | dimensionless | 4 | In general, excluding AA Tau as discussed before, we note that the percentage difference between dynamical masses and the DISCMINER ones is of the order of $\sim 5\%$. |
| Substructure-model velocity perturbations | 50-70 | not stated | m/s | 3 | The corresponding velocity perturbations are of the order of 50-70 m/s. |

## Qualitative findings

- The massive disks are gravitationally stable.  
  > "The massive disks in our sample show $Q>1$, meaning that they all are gravitationally stable." (Gravitational instability?)
- AA Tau is an outlier requiring caution.  
  > "Despite excluding the outer region, the results for AA Tau still appear unusual, with the derived mass of the disk significantly high, marking AA Tau as an outlier in our sample." (Rotation curve fits); "While we include the results for completeness, they should be interpreted with caution due to these reasons." (Rotation curve fits)
- Substructures affect scale radius most; the tested correction stays within typical uncertainties and the dynamical-mass impact is minimal.  
  > "Our results show that the most affected parameter is the scale radius, as it is directly influenced by the pressure gradient." (Model for the rotation curve); "However, the correction remains within the typical uncertainties." (Model for the rotation curve); "In contrast, the impact of substructures on the dynamical mass estimates is minimal." (Model for the rotation curve)
- Theoretical CO radii are systematically too large; inherited depleted CO abundances improve agreement for most sources.  
  > "We observe that the theoretical expectations systematically overestimate the CO radius." (Gas based measurement); "For most of the sources, using these CO abundances result in a better agreement with the observed values." (Gas based measurement)
- Dust substructures may mitigate radial drift.  
  > "This suggests that pressure-modulated substructures may mitigate radial drift." (Conclusions)
- Effective-alpha uncertainty is dominated by accretion-rate uncertainty.  
  > "Our analysis indicates that the uncertainties in $\alpha_S$ are predominantly influenced by the uncertainties in the accretion rate, $\dot{M}_{\star}$." (Transport of angular momentum - effective $\alpha_S$)

## Claim tuples

- H: Rotation curves can constrain disk masses and assess gravitational stability. | E: Fit thermally stratified rotation curves including self-gravity and compute Toomre Q. | R: Ten dynamical disk-mass estimates; seven disk-to-star mass ratios above 5%; massive disks have Q>1. | F: The analyzed disks are gravitationally stable, with three masses below the method's reliable detection threshold. | **supported**
- H: Dynamical gas masses and continuum dust masses imply the standard gas-to-dust ratio. | E: Divide dynamical disk masses by inherited optically thin continuum dust masses. | R: Average gas-to-dust ratio approximately 400. | F: Ratios exceed 100; underestimated dust masses are a likely explanation. | **partially**
- H: Dust radii relative to dynamical scale radii reveal the influence of radial drift and substructures. | E: Compare dust 68%-flux radii with fitted scale radii and disk-evolution expectations. | R: Average dust-radius to scale-radius ratio is 0.75. | F: Pressure-modulated substructures may mitigate radial drift. | **partially**
- H: CO depletion can explain the discrepancy between predicted and observed CO radii. | E: Predict CO radii from dynamical mass and scale radius, then apply independently inferred CO abundances. | R: Initial predictions overestimate CO radii; depletion improves agreement for most sources. | F: The discrepancy may indicate CO depletion. | **partially**
- H: Non-Keplerian contributions materially affect stellar-mass estimates. | E: Compare dynamical stellar masses with DISCMINER masses based on stellar gravity alone. | R: Typical differences are approximately 5%, excluding AA Tau, with deviations in both directions. | F: Including pressure gradients and disk self-gravity provides more accurate stellar-mass estimates. | **supported**
- H: Dynamical disk properties and stellar accretion rates constrain effective angular momentum transport. | E: Calculate effective alpha_S assuming self-similar evolution. | R: Effective alpha_S spans 10^-5 to 10^-2. | F: Transport efficiencies span a broad range; different mechanisms or accretion variability are possible explanations. | **partially**

## Reasoning

- Why this data: Well-defined emitting surfaces and absence of non-axisymmetric features are required for rotation-curve extraction and centrifugal balance.  
  > "the crucial criteria are the availability of well-defined and precisely measured CO emitting surfaces along which to appropriately sample the rotation curve" (Sample); "the absence of non-axisymmetric features, which may affect the azimuthal averaging, intrinsic to the definition of rotation curve, and the very assumption of centrifugal balance." (Sample)
- Why this method: Thermal stratification is needed because a vertically isothermal model cannot explain the shift between the two isotopologue rotation curves.  
  > "The need for including thermal stratification is justified in (cite: Stadler_exoALMA), showing that the shift between $^{12}$CO and $^{13}$CO rotation curves can not be explained by a vertical isothermal model." (Physical model)
- Alternative: Vertically isothermal model rejected for explaining the isotopologue rotation-curve shift.  
  > "the shift between $^{12}$CO and $^{13}$CO rotation curves can not be explained by a vertical isothermal model." (Physical model)
- Alternative: Gaussian density gaps and rings tested in LkCa15 with self-consistent pressure gradient and self-gravity.  
  > "Specifically, we modelled the density variations associated with gaps and rings as Gaussians and then computed the pressure gradient and disc self-gravity self-consistently." (Model for the rotation curve); "We applied this approach to the rotation curve of a reference disc, LkCa 15, fitting the data both with and without the inclusion of substructures." (Model for the rotation curve)
- Alternative: For below-threshold disk masses, use the fitted value or M_d=0.05 M_star as an upper limit.  
  > "One can decide whether to employ the best fit value we report, or to use $M_d=0.05M_\star$ as an upper limit." (Disk masses)
- Alternative: Reduced CO abundance considered to reconcile theoretical and observed CO radii.  
  > "we see that reducing the CO abundance brings the theoretical values closer to the observed ones." (Gas based measurement)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity data are treated as uncorrelated despite finite-beam and extraction-induced correlations.  
  > "Although this is not entirely true because of the finite beam size and of the rotation curve extraction procedure, quantifying the correlation between the data is beyond the scope of the paper." (DySc Code and statistical framework)
- Limitation (authors): Fixing gamma=1 underestimates uncertainties and can bias the scale radius.  
  > "All the fits are performed fixing the power law coefficient of the surface density $\gamma=1$, underestimating the true uncertainties." (DySc Code and statistical framework); "In addition, this choice introduces a potential bias on the scale radius, that is the parameter most affected by the choice of $\gamma$, while the disk and stellar masses are not (cite: Andrews24)." (DySc Code and statistical framework)
- Limitation (authors): Geometrical parameters, emitting-layer heights and disk centering can contribute systematic uncertainty.  
  > "In principle, the geometric parameters (inclination $i$ and position angle PA) and the height of the emitting layer can contribute to the systematic uncertainties." (Systematic uncertainties); "Additionally, as pointed out in (cite: Andrews24), the position of the center of the disk may induce significant uncertainties" (Systematic uncertainties)
- Limitation (authors): J1852, PDS66 and V4046 have fitted disk masses below the approximately 5% disk-to-star measurability threshold.  
  > "As outlined by (cite: veronesi24; Andrews24), the minimum detectable disk-to-star mass ratio with this method is approximately 5%." (Disk masses); "In our sample, only three sources —J1852, PDS66, and V4046— have best-fit disk mass values below this threshold." (Disk masses)
- Limitation (authors): AA Tau outer emission is contaminated by diffuse backside emission; the model cannot account for the emitting-height drop.  
  > "the signal coming from the outer disk of AA Tau is contaminated by the backside diffuse emission." (The case of AA Tau); "leads to a systematic shift of the best fit parameters, since our model can not take this into account." (Rotation curve fits)
- Limitation (authors): Optically thin continuum assumptions can underestimate dust masses.  
  > "dust masses computed in (cite: Curone_exoALMA) underestimate the total dust mass, because of the optically thin emission hypothesis." (Gas to dust ratio)
- Limitation (authors): Toomre-Q inference uses extrapolated midplane temperatures.  
  > "We underline that the temperature at the midplane is extrapolated from the 2D thermal structures (cite: Galloway_exoALMA)." (Gravitational instability?)
- Limitation (authors): The adopted thermochemical radius relation does not explicitly state its CO-abundance dependence.  
  > "There, the dependence on CO abundance is not explicitly stated." (Gas based measurement)
- Limitation (authors): Effective alpha_S does not uniquely imply turbulence-driven accretion.  
  > "Additionally, the formula does not imply that accretion is driven by turbulence; the values it returns should be interpreted as an effective $\alpha_S$, i.e. the amount of transported angular momentum." (Transport of angular momentum - effective $\alpha_S$)
- Caveat (inferred, ours): Table 1 gives DM Tau M_star=0.468 M_sun, while the angular-momentum discussion calls 0.456 M_sun its best fit; use Table 1 as the primary answer key and retain the discrepancy.
- Caveat (inferred, ours): The printed likelihood has ambiguous summation and normalization placement; verify the implementation before reproducing it.
- Caveat (inferred, ours): The geometric and thermal uncertainty treatment should be distinguished from a complete propagation of all systematic errors.
- Caveat (inferred, ours): Below-threshold disk masses and derived ratios should not be treated as secure mass detections solely because their fitted intervals are narrow.
- Caveat (inferred, ours): The substructure robustness experiment is described for one reference disk, limiting generalization across the sample.
- Caveat (inferred, ours): The reported average gas-to-dust ratio lacks an explicit averaging prescription and uncertainty.
- Caveat (inferred, ours): The manuscript uses different figure references for the depleted-CO comparison; identify the plotted data directly.
- Caveat (inferred, ours): Table 3 cites ingleby13, whereas the reference-list key is ingleby13 spelled with an initial i followed by n in the author name Ingleby but indexed as ingleby13 only in the table citation; the supplied reference marker is ingleby13's differing form ingleby13 in prose conversion and should be resolved from the actual bibliography.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: DYSC repository: https://github.com/crislong/DySc; version not stated.  
  > "https://github.com/crislong/DySc" (Rotation curve fits)
- Missing: Explicit public-data statement or product-access instructions.
- Missing: Calibrated/default cubes and the calibration/imaging recipe.
- Missing: Machine-readable rotation curves, uncertainties, masks and adopted distances.
- Missing: Joint thermal posterior samples from the companion analysis.
- Missing: DYSC version or commit, execution configuration and numerical model settings.
- Missing: Posterior aggregation and interval conventions for the 100 repeated fits.
- Missing: Continuum dust-mass assumptions, source-specific CO depletion and 90%-flux-radius inputs from companion papers.
- Missing: Resolution of the DM Tau stellar-mass inconsistency and printed-likelihood ambiguity.
- Data volume (inferred): Cannot estimate bytes from the supplied text; cube dimensions, channel counts and visibility volume are absent.
- Score (inferred): 5/5, 5/10: project code, model, priors, sampler lengths and numeric outputs are supplied, but processing and several essential inputs are delegated to companion papers.
- Rediscovery candidate: no, Numeric answer keys are available, but public availability is not stated and the supplied text does not provide a complete executable recipe or all required input products.

## Links

- Method: (cite: Lodato23) (Rotation-curve model including pressure gradients and disk self-gravity.)
- Method: (cite: martire24) (Thermally stratified rotation-curve model and earlier DYSC application.)
- Method: (cite: Lyndenbell74) (Self-similar surface-density solution.)
- Method: (cite: Dartois03) (Vertical temperature prescription.)
- Method: (cite: emcee) (MCMC library used by DYSC.)
- Method: (cite: discminer1; discminer2) (Rotation-curve extraction methods.)
- Method: (cite: veronesi24; Andrews24) (Dynamical-mass uncertainties and disk-to-star detection threshold.)
- Method: (cite: toomre64; linshu64) (Gravitational-stability criterion.)
- Method: (cite: toci23; trapman23) (Thermochemical CO-radius relation.)
- Method: (cite: hartmann98) (Effective-alpha relation using accretion and disk properties.)
- Companion: (cite: Stadler_exoALMA) (Rotation curves, default cubes, thermal-stratification motivation and inner radial exclusion.)
- Companion: (cite: Izquierdo_exoALMA) (DISCMINER emitting surfaces, geometrical inputs and gas centering.)
- Companion: (cite: Galloway_exoALMA) (Thermal parameters, posterior distributions, gas radii and backside-emission diagnostics.)
- Companion: (cite: Curone_exoALMA) (Dust masses, dust radii, continuum centering and substructures.)
- Companion: (cite: Teague_exoALMA) (DISCMINER stellar-mass comparison.)
- Companion: (cite: Trapman_exoALMA) (Independent chemical masses and CO-depletion estimates.)
- Companion: (cite: Rosotti_exoALMA) (CO-depletion inference tied to the dynamical masses.)
- Related: exoALMA
- Related: MAPS

## Checks

```json
{
 "quotes": 246,
 "quotes_ok": 246,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 63,
 "numeric_problems": 0,
 "fill": {
  "facts": 179,
  "stated": 104,
  "rate": 0.581
 },
 "evidence_ok": true
}
```
