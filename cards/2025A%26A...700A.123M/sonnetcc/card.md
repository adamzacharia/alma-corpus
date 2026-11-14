# Reconciling extragalactic star formation efficiencies with theory: Insights from PHANGS

`2025A&A...700A.123M` | Astronomy and Astrophysics 2025 | first author: Meidt, Sharon E. | arXiv: 2505.19832 | DOI: 10.1051/0004-6361/202453564

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation, nearby_galaxies
- Question: Identify factors that improve the match between turbulence-regulated star formation theories and the star formation efficiency per free-fall time observed in PHANGS galaxies  
  > "Our goal in this paper is to identify factors that can improve the match between turbulence-regulated star formation theories and the behavior observed in galactic and extragalactic cloud populations." (Introduction)
- Target **PHANGS galaxy sample: 67 galaxies, 841 high-completeness 1.5 kpc hexagonal regions**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00650.S, 2013.1.00803.S, 2013.1.01161.S, 2015.1.00121.S, 2015.1.00782.S, 2015.1.00925.S, 2015.1.00956.S, 2016.1.00386.S, 2017.1.00392.S, 2017.1.00766.S, 2017.1.00886.L, 2018.1.01321.S, 2018.1.01651.S, 2018.A.00062.S, 2019.1.01235.S, 2019.2.00129.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 150 pc beam FWHM (fixed physical scale, fiducial cloud-scale measurement)  
  > "we adopt a beam full-width-half-maximum scale corresponding to $D_{beam}=150$ pc as our fiducial measurement scale" (Cloud-scale gas properties)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA data processed as part of the PHANGS-ALMA CO (2-1) survey  
  > "This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA CO (2-1) survey" (Acknowledgements)
- Line: CO (2-1) (not stated)
- External data: PHANGS high-level measurement database: star formation rates, gas surface densities, cloud-scale properties and free-fall times in 1.5 kpc hexagonal regions  
  > "The information needed to test the cloud-scale factors influencing the process of star formation is currently accessible in the PHANGS high-level measurement database presented by (cite: sun22) and used by (cite: leroy24)." (A cloud population-averaged (time-averaged) view of the star formation cycle) [from (cite: sun22); (cite: leroy24)]
- External data: Completeness correction (f_comp threshold) applied to select high-completeness regions  
  > "We also take into account the completeness correction advised by (cite: leroy24) and developed by (cite: sun23)" (A cloud population-averaged (time-averaged) view of the star formation cycle) [from (cite: leroy24); (cite: sun23)]
- External data: CO-to-H2 conversion factor alpha_CO^{2-1}  
  > "we follow (cite: leroy24) and adopt the new CO-to-H$_2$ conversion factor $\alpha_{\rm CO}^{2-1}$ recommended by (cite: schinnerLeroyReview)" (A cloud population-averaged (time-averaged) view of the star formation cycle) [from (cite: schinnerLeroyReview); (cite: leroy24)]
- External data: Galaxy rotation curves from CO kinematics, with Legendre polynomial fits (Nofech et al., in prep.)  
  > "Following (cite: sun23) we adopt Legendre polynomial fits (Nofech et al., in prep.) to each of the (cite: lang20) rotation curves measured for each galaxy from the observed CO kinematics in a series of 150pc-wide radial bins." (The background galactic potential: constraining where gas becomes self-gravitating) [from (cite: lang20); (cite: sun23); Nofech et al., in prep.]
- External data: Logarithmic derivative of the rotation curve (beta) per hexagonal region  
  > "obtained from each polynomial curve at that location, as tabulated by (cite: sun23)" (The background galactic potential: constraining where gas becomes self-gravitating) [from (cite: sun23)]
- External data: PHANGS 2D stellar mass surface density maps  
  > "we follow (cite: sun20) and adopt the PHANGS 2D stellar mass surface density maps and assume a constant scale height" (The background galactic potential: constraining where gas becomes self-gravitating) [from (cite: sun20)]
- External data: Mean power-law slope of resolved local clouds (alpha = 1.8) used as initial value in the fit  
  > "the mean value determined for the resolved clouds analyzed by (cite: Kainulainen14)" (The optimized hybrid LN+PL PDF models) [from (cite: Kainulainen14)]
- External data: Canonical core-to-star efficiency epsilon_core ~ 0.3-0.5  
  > "Observations and simulations (cite: enoch08; sadavoy10; alves07; andre10; matzner) suggest relatively high canonical values $\epsilon_{\rm core}\sim0.3-0.5$." (Comparison with theoretical predictions) [from (cite: enoch08; sadavoy10; alves07; andre10; matzner)]
- External data: Self-gravitation threshold gamma(k=0) ~ 2.5 (collapse in the galactic potential)  
  > "(cite: meidt18) estimate that this coincides with $\gamma(k=0)\approx2.5$" (Practical considerations) [from (cite: meidt18)]

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
- smoothing: Sigma_mol and Sigma_SFR maps convolved to a Gaussian kernel with FWHM equal to the hex diameter, sampled at the hex centre  
  > "these measurements are extracted from maps of $\Sigma_{\rm mol}$ and $\Sigma_{\rm SFR}$ that have been convolved to share a matched Gaussian kernel with FWHM equal to the hex diameter" (footnote 2)
- final beam: 150 pc beam FWHM (fiducial cloud-scale measurement scale)  
  > "we adopt a beam full-width-half-maximum scale corresponding to $D_{beam}=150$ pc as our fiducial measurement scale" (Cloud-scale gas properties)
- final rms: _not stated_

### Inherited from earlier work

- kpc-scale SFR and molecular gas surface density matching to reconstruct eps_ff  
  > "Following (cite: leroy24), as well as (cite: leroy17), (cite: utomo18) and (cite: sun22), each kpc-scale SFR measurement is matched with a kpc-scale molecular gas surface density" (A cloud population-averaged (time-averaged) view of the star formation cycle) [from (cite: leroy24); (cite: leroy17); (cite: utomo18); (cite: sun22)]
- Details of the multi-wavelength measurements (SFRs, gas surface densities, free-fall times)  
  > "We refer the reader to (cite: sun23) and (cite: leroy24) for details." (A cloud population-averaged (time-averaged) view of the star formation cycle) [from (cite: sun23); (cite: leroy24)]
- Constant vertical size h = 100 pc  
  > "Following (cite: sun23; leroy24) we assume a constant vertical size $h=100$ pc." (A cloud population-averaged (time-averaged) view of the star formation cycle) [from (cite: sun23; leroy24)]
- CO-to-H2 conversion factor alpha_CO^{2-1}  
  > "we follow (cite: leroy24) and adopt the new CO-to-H$_2$ conversion factor $\alpha_{\rm CO}^{2-1}$ recommended by (cite: schinnerLeroyReview)" (A cloud population-averaged (time-averaged) view of the star formation cycle) [from (cite: leroy24); (cite: schinnerLeroyReview)]
- High-completeness selection: f_comp > 0.5 and cloud-scale Sigma_mol > 20 Msun pc^-2  
  > "with the threshold criteria $f_{\rm comp}>0.5$ and $\langle\Sigma_{\rm mol}^{\rm cloud}\rangle>20$ $M_\odot$ pc$^{-2}$" (A cloud population-averaged (time-averaged) view of the star formation cycle) [from (cite: leroy24)]
- Representative cloud-scale pixel per hexagon from mass-weighted PHANGS-ALMA CO(2-1) cloud-scale properties  
  > "whose properties are defined by the mass-weighted average properties of the cloud-scale regions probed in our PHANGS-ALMA CO(2-1) maps within that zone (cite: sun18; sun20a; leroy24)" (Cloud-scale gas properties) [from (cite: sun18; sun20a; leroy24)]
- Turbulent driving parameter b = 0.87 and beta = 1, adopted for compatibility with a reference whose name is missing in the text  
  > "In what follows we adopt $b=0.87$ and $\beta=1$ for compatibility with" (Comparison with theoretical predictions) [from reference name missing in the paper text (blank after 'compatibility with')]
- phi_t = 1.9 for the LN SFF/MFF models, calibrated in an earlier work whose name is missing in the text  
  > "we adopt the value $\phi_t=$1.9 calibrated by" ('Single free fall' predictions) [from reference name missing in the paper text (blank after 'calibrated by')]

### Not stated but needed to reproduce (our reading)

- Exact version/release of the PHANGS high-level measurement database and the table of the 841 region values (Sigma_SFR, Sigma_mol, cloud-scale sigma, alpha_vir, Sigma_cloud, galactocentric radius) is not given
- Which SFR tracer combination and calibration (Halpha, FUV, 24 um) was used for Sigma_SFR is not stated here
- Numerical value or prescription of alpha_CO^{2-1} (including any metallicity or surface-density dependence) is not given
- Which version and masking of the PHANGS-ALMA CO(2-1) cubes (resolution, sensitivity, moment-map products) feed the cloud-scale properties is not stated
- Galactocentric radius bin widths used before splitting into 30th/70th percentile groups are not given
- No weights, uncertainties or error treatment in the curve_fit regression, and no uncertainty on the fitted alpha per group, are stated
- Legendre polynomial rotation-curve fits are 'in prep.' (Nofech et al.) and not available from this paper
- The stellar scale-height scaling relation is attributed to 'X' (citation missing) and the adopted scale heights are not listed
- References for b = 0.87, beta = 1 and phi_t = 1.9 are missing in the text; phi_x = 1.12 is only 'calibrated by using numerical simulations'
- Source files for the cloud-scale quantities (Mach number, virial parameter, velocity dispersion) are not named beyond 'the database'

## Analysis recipe

1. **Reconstruct observed eps_ff per 1.5 kpc region**: Match kpc-scale SFR and molecular gas surface density in 1.5 kpc hexagons and compute eps_ff^obs = t_ff * Sigma_SFR/Sigma_mol, with t_ff from the mass-weighted cloud-scale gas density in each region  
  > "The latter are essential for constraining the gas free-fall time, which makes it possible with this approach to observationally reconstruct the efficiency per free-fall time as" (A cloud population-averaged (time-averaged) view of the star formation cycle); "Following (cite: leroy24), as well as (cite: leroy17), (cite: utomo18) and (cite: sun22), each kpc-scale SFR measurement is matched with a kpc-scale molecular gas surface density" (A cloud population-averaged (time-averaged) view of the star formation cycle)
   - parameter: 1.5 kpc hexagonal regions  
  > "measurements are extracted in hexagonal regions 1.5 kpc in size" (A cloud population-averaged (time-averaged) view of the star formation cycle)
   - parameter: h = 100 pc; rho_cloud = Sigma_cloud / 2h  
  > "Again, we use the fixed molecular gas scale height $h = 100$ pc to determine the gas volume density $\langle\rho_{\rm mol}^{\rm cloud}\rangle$=$\langle\Sigma_{\rm mol}^{\rm cloud}\rangle/2h$" (Cloud-scale gas properties)
   - parameter: Keep regions with f_comp > 0.5 and cloud-scale Sigma_mol > 20 Msun pc^-2, giving 841 regions in 67 galaxies  
  > "with the threshold criteria $f_{\rm comp}>0.5$ and $\langle\Sigma_{\rm mol}^{\rm cloud}\rangle>20$ $M_\odot$ pc$^{-2}$" (A cloud population-averaged (time-averaged) view of the star formation cycle); "This yields $841$ regions sampling across the targets set of $67$ galaxies." (A cloud population-averaged (time-averaged) view of the star formation cycle)
   - assumption: Sound speed c_s = 0.3 km/s (20 K) for the turbulent Mach number  
  > "which we use to estimate the turbulent Mach number assuming a sound speed $c_s = 0.3$ km s$^{-1}$ (corresponding to a temperature of 20 K)" (Cloud-scale gas properties)
   - assumption: Fixed 150 pc beam FWHM scale and fixed scale height h = 100 pc for the representative cloud  
  > "we adopt a beam full-width-half-maximum scale corresponding to $D_{beam}=150$ pc as our fiducial measurement scale" (Cloud-scale gas properties)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate self-gravity vs galactic potential (gamma) and the self-gravitation threshold per region**: Compute gamma (cloud self-gravity relative to the background potential) from cloud-scale Sigma, with kappa, Omega, nu from rotation curves and stellar mass density; derive rho_G and t_stop from gamma_0 and gamma_G  
  > "using the observed galaxy rotation curve and the stellar mass density, in addition to the observed gas properties" (The background galactic potential: constraining where gas becomes self-gravitating)
   - parameter: gamma_G(k=0) ~ 2.5 threshold for onset of self-gravitation  
  > "We thus designate $\gamma_{\rm G}(k=0)\approx2.5$ as the uniform-density criterion for the onset of self-gravitation." (Practical considerations)
   - parameter: Triaxial cloud with axis ratio q ~ 1 and power-law density rho ~ r^-k  
  > "assuming that the gas is arranged with a triaxial geometry (with cloud vertical extent $Z_c=qR_{\rm c}$ where the axis ratio $q\sim1$) and follows a power-law density distribution $\rho\propto r^{-k}$" (Additional empirical constraints from PHANGS)
   - parameter: Constant stellar scale height z0 for rho_stars from PHANGS stellar mass surface density maps  
  > "we follow (cite: sun20) and adopt the PHANGS 2D stellar mass surface density maps and assume a constant scale height" (The background galactic potential: constraining where gas becomes self-gravitating)
   - assumption: Dark matter and atomic gas ignored; total density = stars + molecular gas  
  > "As our focus is on the inner, molecule-rich star-forming parts of the disk, we ignore dark matter and the contribution from atomic gas" (The background galactic potential: constraining where gas becomes self-gravitating)
   - fitting: _not stated_
   - validation: _not stated_
3. **Set up the sgMFF efficiency model with a kinked LN+PL density PDF and finite PDF renewal**: Hybrid LN+PL PDF with transition density s_t = s_G (not tied to alpha), star formation restricted to the PL gas, and PDF renewal limited to t_stop = t_ff at rho_G, giving the factor gamma_0/gamma_G in eps_ff  
  > "Instead, we test the $s_t$ value implied by the criterion for self-gravity to dominate the external galactic potential determined by (cite: meidt20), i.e. $s_t=s_{\rm G}=\ln (\rho_G/\rho_0)$" (Summary of the proposed modelling strategy); "we assume that the density PDF is in a steady-state only until the free-fall time at the threshold density for self-gravitation $\rho_{\rm G}$, i.e. $t_{\rm stop}=t_{\rm ff,G}$" (A finite reservoir to undergo collapse and replenish the PDF)
   - parameter: b = 0.87, c_s = 0.3 km/s, epsilon_core = 0.5 in all four tested models  
  > "In all four tested models, we adopt $b=0.87$ for the turbulent driving parameter, $c_s=0.3$ km s$^{-1}$ and $\epsilon_{\rm core}=0.5$ but comment on the impact of variation in these parameters, where applicable." (The optimized hybrid LN+PL PDF models)
   - parameter: phi_t set to unity for the LN+PL formulation  
  > "here $\phi_t$ is omitted (set to unity)" (Summary of the proposed modelling strategy)
   - parameter: Comparison models: MFF and SFF with the smooth hybrid PDF (s_t = s_crit) and the same inputs  
  > "We also compare with MFF and SFF predictions using the hybrid smooth-PDF of (cite: burk18) and (cite: burkmocz) with $s_t=s_{\rm crit}$, adopting identical values for all mutual input parameters." (The optimized hybrid LN+PL PDF models)
   - assumption: t_obs approximated by the cloud free-fall time t_ff(rho_0) for long-visibility SFR tracers  
  > "suggesting that, with long-visibility tracers, the minimum window of time that each individual cloud is probed can be well approximated by the cloud free-fall time $t_{\rm ff}(\rho_0)$" (Prescriptions for t_obs appropriate for long visibility star formation tracers)
   - assumption: Cloud number per 1.5 kpc region approximately conserved, so the time between cloud formation events is negligible  
  > "we assume for the purposes of the discussion in this paper that the number of clouds within each (high-completeness) 1.5 kpc region is approximately conserved" (Prescriptions for t_obs appropriate for long visibility star formation tracers)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit the power-law slope alpha to eps_ff^obs in galactocentric-radius and surface-density groups**: Non-linear least squares fit of alpha, the only free parameter, per group of regions (radius bins, each split by 30th and 70th percentiles of cloud-scale Sigma_mol); all regions in a group get the same alpha  
  > "is determined using non-linear least squares regression, specifically the `curve_fit` routine in the `scipy.optimize` `Python` package" (The optimized hybrid LN+PL PDF models); "each bin is further divided into three groups: below the 30$^{th}$ percentile of the molecular gas surface density distribution at that radius, between the 30$^{th}$ and 70$^{th}$ percentiles and above the 70$^{th}$ percentile" (The optimized hybrid LN+PL PDF models)
   - software: Python, scipy.optimize.curve_fit
   - parameter: Bounds 1.5 < alpha < 5, initial alpha = 1.8  
  > "The regression is bounded to $1.5<\alpha<5$ and given an initial input of $\alpha=1.8$" (The optimized hybrid LN+PL PDF models)
   - assumption: Width of the LN part fixed by the observed cloud-scale Mach number; sigma_s, s_crit and s_t set empirically from observations, alpha the only free variable  
  > "we constrain $\sigma_s$, $s_{\rm crit}$ and $s_{t}=\ln{\rho_g/\rho_0}$ empirically" (Using the comparison between the model and the observations to constrain alpha)
   - fitting: scipy.optimize curve_fit, bounded least squares, initial alpha 1.8; priors, weights and likelihood not stated  
  > "The regression is bounded to $1.5<\alpha<5$ and given an initial input of $\alpha=1.8$" (The optimized hybrid LN+PL PDF models)
   - validation: Grouped fit gives a better match than using all measurements at a given radius; effect of neglecting time evolution in alpha estimated at <10% for 1.5<alpha<2.5  
  > "In testing, we have found that allowing for systematic variation in $\alpha$ of this kind yields a better match to the observations than when, e.g., all measurements at a given radius are used to constrain $\alpha$." (The optimized hybrid LN+PL PDF models); "This translates into less than 10% error in the $\alpha$ determined by fitting to $\epsilon_{\rm ff}$" (Coordination of cloud evolutionary stage?)
5. **Compute structural diagnostics from the fitted PDFs (dense gas fraction, self-gravitating fraction)**: Compute the dense gas fraction above n_d = 10^3 cm^-3 and the PL (self-gravitating) mass fraction from each fitted hybrid PDF and compare with observed HCN/CO dense gas fractions  
  > "The middle column shows the dense gas fractions $f_d$ measured from each hybrid PDF above a fixed dense gas density threshold $n_d=10^3$ cm$^{-3}$, near the effective critical density of HCN(1-0)" (Dense gas content)
   - parameter: f_sg = fraction of gas in the PL portion of the density PDF  
  > "The right column shows the self-gravitating gas fractions $f_{\rm sg}$ measuring the fraction of gas in the PL portion of the density PDF." (Dense gas content)
   - fitting: _not stated_
   - validation: Fiducial model f_d compared with observed dense gas fractions from HCN/CO  
  > "The top middle panel exhibits good correspondence with the observed values of the dense gas fraction traced by HCN/CO and its empirical relation to gas surface density found by (cite: neumann23)." (Dense gas content)
6. **Calibrate an empirical alpha vs alpha_vir relation**: alpha = 1.5 + R_alpha / log(alpha_vir) with R_alpha set from the mean and rms of (alpha - 1.5) log alpha_vir over the fitted groups  
  > "with the value $\mathcal{R_\alpha}=0.23\pm0.06$, chosen from the mean and rms of $(\alpha-1.5)\log\alpha_{\rm vir}$ measured across the plotted data points" (Discussion: systematic variation in alpha)
   - parameter: Relation asymptotes to alpha = 1.5 at large alpha_vir  
  > "chosen to asympotote to $\alpha=1.5$ at large $\alpha_{\rm vir}$" (Discussion: systematic variation in alpha)
   - fitting: _not stated_
   - validation: Relation is purely empirical and valid only together with the nominal model  
  > "it is purely empirical and applies only together with our nominal model" (Discussion: systematic variation in alpha)
7. **Compare the calibrated sgMFF model with KM05 SFF and FK12 MFF trends**: Plot eps_ff vs sigma at fixed alpha_vir and fixed Sigma for three models, using trend lines at the 10th, 50th and 90th percentiles of the observed distributions, over the PHANGS data  
  > "The three models are: the calibrated sgMFF model proposed in this work (top), the KM05 SFF model (middle), and the FK12 MFF model (bottom) scaled by a factor of 1/100." (Predictions of the PHANGS-calibrated sgMFF model); "three trend lines are drawn at three different representative values, chosen from the 10th, 50th and 90th percentiles of the observed distributions" (Predictions of the PHANGS-calibrated sgMFF model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **scipy.optimize (curve_fit)** : Non-linear least squares fit of the power-law slope alpha to eps_ff^obs  
  > "is determined using non-linear least squares regression, specifically the `curve_fit` routine in the `scipy.optimize` `Python` package" (The optimized hybrid LN+PL PDF models)
- **Python** : Environment of the scipy.optimize regression  
  > "specifically the `curve_fit` routine in the `scipy.optimize` `Python` package" (The optimized hybrid LN+PL PDF models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of high-completeness 1.5 kpc regions | 841 | not stated | regions | 1 | This yields $841$ regions sampling across the targets set of $67$ galaxies. |
| Median gamma (k=0) on the 150 pc cloud scale | 1.1 (mean 1.08) | not stated | dimensionless | 2 | From the median (mean) $\gamma_{k=0}=1.1$ ($\gamma_{k=0}=1.08$), we infer that gas self-gravity and the galactic potential are comparably strong on the cloud scale. |
| Range of gamma (k=0) from inner radii to outer | ~0.5 to ~2 | not stated | dimensionless | 2 | Values range from $\gamma_{k=0}\sim0.5$ at inner radii to $\gamma_{k=0}\sim2$. |
| Typical self-gravitation threshold density rho_G | ~3 Msun pc^-3 (n ~ 100 cm^-3) | not stated | Msun pc^-3 | 2 | we find $\rho_{\rm G}\sim3$ M$_{\rm \odot}$ pc$^{-3}$ (or $n\sim 100$ cm$^{-3}$) |
| ln(rho_G/rho_0) for typical gamma_0 | 0.4-3.2 | not stated | dimensionless | 2 | this makes $\ln \rho_{\rm G}/\rho_0\approx 0.4-3.2$, placing $\rho_{\rm G}$ towards the outer edge |
| Fitted PL slope alpha, fiducial sgMFF model | ~1.6-2.5 (k ~ 1.2-1.9) | not stated | dimensionless | 4 | makes it possible to match the $\epsilon_{\rm ff}$ with lower $\alpha\sim1.6-2.5$ (higher $k\sim1.2-1.9$) |
| Fitted PL slope alpha, MFF smooth-PDF model, with LN-to-PL transition density | alpha ~2.5-3; ln(rho_t/rho_0) ~10-15 | not stated | dimensionless | 4 | In the MFF smooth-PDF model, which has the highest values for $\alpha\sim2.5-3$ ($k=1-1.2$), the transition from LN to PL is placed at densities $\ln (\rho_t/\rho_0)\sim10-15$ |
| LN-to-PL transition density in the fiducial model | ln(rho_t/rho_0) ~1-3 | not stated | dimensionless | 4 | several orders of magnitude higher than in the fiducial model ($\ln (\rho_t/\rho_0)\sim1-3$ |
| Typical alpha in galaxy centres | ~1.6 | not stated | dimensionless | 4 | any clouds with higher $\alpha$ (less dense gas) than typical ($\alpha_{\rm ctr}\approx 1.6$) |
| Typical alpha in main disk | ~2 | not stated | dimensionless | 4 | there appears to be a real absence of clouds with $\alpha$ below the typical $\alpha_{\rm disk}\approx 2$ |
| Error in fitted alpha from neglecting time evolution (1.5<alpha<2.5) | <10% | not stated | percent | 4 | This translates into less than 10% error in the $\alpha$ determined by fitting to $\epsilon_{\rm ff}$ |
| Self-gravitating (PL) mass fraction in the fiducial models | roughly a third to a half | not stated | dimensionless | 5 | the PL represents a large portion of the total mass distribution (roughly a third to a half |
| Scaling factor R_alpha in alpha = 1.5 + R_alpha/log(alpha_vir) | 0.23 | 0.06 | dimensionless | 6 | with the value $\mathcal{R_\alpha}=0.23\pm0.06$, chosen from the mean and rms of $(\alpha-1.5)\log\alpha_{\rm vir}$ measured across the plotted data points |

## Qualitative findings

- MFF scenarios match observed cloud populations best when the density PDF contains a prominent power-law component, with no artificial reduction in epsilon_core  
  > "we conclude that MFF scenarios provide their best match to observed cloud populations when the density distribution includes a prominent PL component, requiring no artificial reduction in $\epsilon_{\rm core}$." (Dense gas content)
- Fitted PL slope increases with cloud-scale surface density and decreases with virial parameter in both best-fitting models  
  > "the power-law slope needed to match PHANGS measurements exhibits an increase with increasing $\langle\Sigma_{\rm mol}^{\rm cloud}\rangle$ and a decrease with increasing virial parameter" (Summary & Conclusions)
- Variation in alpha could alternatively reflect coordination of cloud evolutionary stage within environment  
  > "Viewing the efficiency variations as originating with time evolution in the power-law slope, our findings would alternatively imply coordination of the cloud evolutionary stage within environment." (abstract)

## Claim tuples

- H: Do PHANGS cloud-scale eps_ff measurements follow the dependence on virial level and velocity dispersion predicted by turbulence-regulated models? | E: Compare PHANGS eps_ff^obs for 841 regions in 67 galaxies with single- and multi-free-fall LN PDF model predictions | R: Little sign of the predicted dependence on virial level and weak variation with cloud-scale velocity dispersion | F: Conventional models are in tension with the observations | **supported**
- H: Self-gravity, a broad PL density tail and finite PDF renewal can bring MFF models into line with PHANGS efficiencies | E: Replace the LN PDF by a kinked LN+PL PDF with transition at the galactic decoupling density and limit PDF renewal to t_stop; fit alpha to eps_ff^obs | R: Predicted MFF efficiencies are significantly reduced compared with pure LN PDFs, and alpha ~1.6-2.5 in the fiducial model matches the data | F: The sgMFF model matches the observed low efficiencies with realistic power-law slopes and no ad hoc lowering of epsilon_core | **supported**
- H: Does the PL slope needed to match eps_ff vary with galactic environment? | E: Fit alpha in groups sorted by galactocentric radius and cloud-scale Sigma_mol, and relate it to alpha_vir | R: alpha rises with Sigma_mol and falls with alpha_vir, with a calibrated relation alpha = 1.5 + R_alpha/log(alpha_vir), R_alpha = 0.23 +/- 0.06 | F: Gas furthest from virial balance contains fractionally more gas at high density; the trend is tied to the choice to let alpha drive the eps_ff variations | **partially**
- H: Do the broad-PL fiducial PDFs give more realistic dense gas content than the smooth-PDF models? | E: Compute dense gas fractions above 10^3 cm^-3 and self-gravitating fractions from each fitted PDF and compare with observed HCN/CO fractions | R: Broad PL PDFs give lower dense gas fractions than smooth-PDFs and agree better with the observed relation to surface density | F: Fiducial broad-PL models are closer to observed extragalactic dense gas fractions | **supported**
- H: How should star formation be modelled in main-sequence disks versus other environments? | E: Compare the calibrated sgMFF model with the KM05 SFF and FK12 MFF models and discuss environment dependence | R: With galaxy regulation included, sgMFF behaves similarly to the virialized-cloud SFF model in main-sequence galaxies | F: Main-sequence star formation can be modelled as approximately virial; the flexible MFF models may be better suited outside regulated disks | **partially**

## Reasoning

- Why this data: PHANGS samples the star formation cycle across diverse environments and so informs how models can be tailored to observations  
  > "which samples the star formation cycle in a diversity of environments, provide insight into how turbulence-regulated star formation models can be tailored to match observations" (Introduction)
- Why this method: kpc-scale eps_ff is preferred because cloud-scale SFR maps would not be more representative given tracer timescales; eps_ff vs sigma is the diagnostic because it uses independent observables  
  > "Such SFR maps would not necessarily furnish more realistic $\epsilon_{\rm ff}$ estimates representative of the local star-forming cycle, though, given the timescales associated with most extragalactic star formation tracers" (A cloud population-averaged (time-averaged) view of the star formation cycle); "is constructed from independent observables, and so we take this as our diagnostic of choice in what follows" (Comparison with theoretical predictions)
- Alternative: Smooth hybrid LN+PL PDF of Burkhart (s_t = s_crit) judged less consistent with observed cloud density structure than the fiducial kinked PDF  
  > "But the absence of a prominent, shallow power-law would still make the MFF and SFF smooth-PDFs defined by (cite: burk18) less consistent with observed cloud density structure than reproduced with our fiducial models." (Dense gas content)
- Alternative: Three alternative eps_ff models examined to assess the quality of the main model  
  > "we thus also examine the $\alpha$ values implied by three alternative $\epsilon_{\rm ff}$ models" (Using the comparison between the model and the observations to constrain alpha)
- How they decided it was enough: _not stated_
- Limitation (authors): Fitted alpha is only as good as the eps_ff model and inherits its uncertainties  
  > "our determinations of $\alpha$ are only as good as the $\epsilon_{\rm ff}$ model, and they inherit the uncertainties associated with factors that are either not well-constrained or incorporated into the model at present." (Using the comparison between the model and the observations to constrain alpha)
- Limitation (authors): Alternative grouping schemes for the alpha fit were not exhaustively tested  
  > "It is worth emphasizing that we have not exhaustively tested alternative sorting schemes" (The optimized hybrid LN+PL PDF models)
- Limitation (authors): t_obs may be underestimated when time between cloud formation events is non-negligible; assumption good to about a factor of two  
  > "This should be good to within a factor of roughly two, but scenarios in which $t_{\rm no~cl}$ represents a non-negligible part of the cloud life-cycle may underestimate $t_{\rm obs}$ more strongly." (Prescriptions for t_obs appropriate for long visibility star formation tracers)
- Limitation (authors): The alpha vs alpha_vir calibration is purely empirical and applies only with the nominal model  
  > "it is purely empirical and applies only together with our nominal model" (Discussion: systematic variation in alpha)
- Caveat (inferred, ours): Fitted alpha values carry no stated uncertainties, and the group-wise fit assigns one alpha to 3 or more regions, which can hide scatter
- Caveat (inferred, ours): The alpha trends with alpha_vir and Sigma are partly built in by letting alpha alone absorb all eps_ff variation; other free parameters (epsilon_core, b, c_s, phi_t, h) are held fixed
- Caveat (inferred, ours): Fixed h = 100 pc, c_s = 0.3 km/s and epsilon_core = 0.5 for all regions, including galaxy centres, may bias alpha
- Caveat (inferred, ours): t_obs = t_ff(rho_0) with negligible gap between clouds is an assumption not tested against measured cloud lifetimes in each region
- Caveat (inferred, ours): No quantitative goodness-of-fit statistic is given for sgMFF versus KM05 or FK12 comparisons; the comparisons are visual
- Caveat (inferred, ours): The ALMA-based inputs come from a prior database and are not re-derived, so ALMA calibration and imaging uncertainties are not propagated

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: The table of 841 region measurements (or the database release) is not provided with the paper
- Missing: Unpublished Legendre-polynomial rotation-curve fits (Nofech et al., in prep.) and the stellar scale-height relation are needed for gamma
- Missing: Radius-bin definitions and the exact curve_fit configuration (weights, uncertainties) for the grouped alpha fit
- Missing: Source for phi_t = 1.9 and b = 0.87 is missing in the text
- Missing: No analysis code is stated as released
- Data volume (inferred): Small (about a megabyte) if the 841-row database table is used; raw PHANGS-ALMA CO(2-1) cubes from 16 ALMA projects would be hundreds of GB but are not needed for this analysis
- Score (inferred): 3/5, The model equations and the alpha-fitting recipe are given in detail, but the input measurements come from external databases and unpublished fits, and several parameter references are missing; results are numeric but mostly model-fit ranges.
- Rediscovery candidate: no, The paper does not state that the input table is public, depends on unpublished rotation-curve fits, and its main results are model-dependent ranges rather than directly measured numbers.

## Links

- Method: (cite: sun22) Sun, J., Leroy A., Schruba, A. et al. 2022, AJ, 164, 43 (PHANGS high-level measurement database and the cloud-scale measurement approach)
- Method: (cite: sun23) Sun, J., Leroy A., Ostriker, E. et al. 2023, ApJ, 945, 19 (Completeness correction, h = 100 pc, rotation-curve beta values and region extraction)
- Method: (cite: leroy24) Leroy, A. K., Sun, J., Meidt, S. E. et al. 2025, ApJ, 985, 14 (Observed eps_ff measurements, alpha_CO choice and completeness thresholds)
- Method: (cite: meidt20) Meidt, S. E., Glover, S. C. O. Kruijssen, J. M. D., et al. 2020, ApJ, 892, 73 (Galactic bottleneck model providing the self-gravitation threshold rho_G)
- Method: (cite: burk18) Burkhart, B. 2018, ApJ, 863, 118 (Smooth hybrid LN+PL PDF formulation used as the comparison model)
- Companion: (cite: leroy24) Leroy, A. K., Sun, J., Meidt, S. E. et al. 2025, ApJ, 985, 14 (Presents the PHANGS eps_ff measurements modelled here)
- Companion: (cite: meidt18) Meidt, S. E., Leroy, A., Rosolowsky, E., et al. 2018, ApJ, 854, 100 (Source of the gamma ~2.5 criterion and the galactic-potential description of super-virial gas)
- Related: PHANGS (Physics at High Angular resolution in Nearby GalaxieS)
- Related: PHANGS-ALMA CO(2-1) survey

## Checks

```json
{
 "quotes": 110,
 "quotes_ok": 110,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 16,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2019.1.01235.S"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 64,
  "rate": 0.582
 },
 "evidence_ok": true
}
```
