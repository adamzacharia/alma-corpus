# Fitting the light curves of Sagittarius A* with a hot-spot model. Bayesian modeling of QU loops in the millimeter band

`2024A&A...685A.142Y` | Astronomy and Astrophysics 2024 | first author: Yfantis, A. I. | arXiv: 2310.07762 | DOI: 10.1051/0004-6361/202348230

Card schema 1.0 | model gpt-6.1-sol | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars
- Question: Constrain collisionless plasma conditions and hot-spot geometry using polarized millimeter light curves.  
  > "Our main goal is to give insight into possible conditions of collisionless plasma around , independent of the GRMHD and GRPIC interpretation." (Introduction); "A byproduct of our fitting procedure is the determination of the spin of , its orientation on the sky, and the observer’s viewing angle geometry." (Introduction)
- Target **Sagittarius A***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01404.V
- bands: _not stated_
- frequencies and spectral setup: 230 GHz  
  > "We focused on 230 GHz data that were collected immediately following an X-ray flare detected by the *Chandra* observatory on April 11 2017 (cite: eht:2022_paperII; Wielgus2022_LC)." (Introduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: April 11, 2017, 9–13 UTC; fitted segment 9:00–10:30 UTC  
  > "ALMA observed on April 11, 2017, from 9 UTC until 13 UTC." (Two-step parameter estimation procedure); "We fit ALMA light curves starting at 9:00 UTC until 10:30 UTC" (Two-step parameter estimation procedure)
- pi or archival as stated: Polarized observations reported by (cite: W22)  
  > "In this work, we fit the polarized observations of near event-horizon emission reported by (cite: W22)" (Introduction)
- Other facility **Chandra**: X-ray flare preceding the modeled ALMA data  
  > "We focused on 230 GHz data that were collected immediately following an X-ray flare detected by the *Chandra* observatory on April 11 2017 (cite: eht:2022_paperII; Wielgus2022_LC)." (Introduction)
- Other facility **COMA computational cluster at Radboud University**: Computational resources  
  > "Using the COMA computational cluster at Radboud University." (Spin estimates)
- External data: Polarized ALMA light curves used for fitting  
  > "In this work, we fit the polarized observations of near event-horizon emission reported by (cite: W22)" (Introduction) [from (cite: W22)]
- External data: April 11 2017 X-ray flare detected by Chandra  
  > "We focused on 230 GHz data that were collected immediately following an X-ray flare detected by the *Chandra* observatory on April 11 2017 (cite: eht:2022_paperII; Wielgus2022_LC)." (Introduction) [from (cite: eht:2022_paperII; Wielgus2022_LC)]
- External data: Black-hole mass measurements bracketing the adopted mass  
  > "We assumed a mass of Sgr A\* $M=4.155 \times 10^6\,M_{\odot}$, which is between the measurements of (cite: 2022A&A...657L..12G) and those of (cite: Do:2019a)." (Model) [from (cite: 2022A&A...657L..12G); (cite: Do:2019a)]
- External data: EHT shadow-ring diameter around 10–11 M, motivating the model field of view  
  > "with the black hole shadow ring diameter observed by the EHT corresponding to around 10-11$M$ (cite: eht:2022_paperI; eht:2022_paperVI)." (Model) [from (cite: eht:2022_paperI; eht:2022_paperVI)]
- Simulation/model as data: Synthetic data for a controlled pipeline-recovery test  
  > "Finally, before fitting the real data, we performed a controlled `bipole` run using synthetic data to demonstrate the ability of our pipeline to recover the truth value." (Two-step parameter estimation procedure)
- Simulation/model as data: Preliminary two-temperature 3D GRMHD simulations of MADs for comparison with inferred spot properties  
  > "Our preliminary experiments with two-temperature 3D GRMHD simulations of MADs do show hot spots with properties matching our estimates of the spot parameters (Jiménez-Rosales et al. in prep.)." (Discussion and conclusions)

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

- Semi-analytic hot-spot model adopted and further developed  
  > "To simulate millimeter emission from the flaring , we adoptede and further developd the semi-analytic model described in full detail by (cite: Vos:2022)." (Model) [from (cite: Vos:2022)]
- Model inspiration  
  > "The model is inspired by work of (cite: Brod-Loeb2006) (see also (cite: Fraga-Encinas:2016nft))." (Model) [from (cite: Brod-Loeb2006); (cite: Fraga-Encinas:2016nft)]
- Published polarized observations reused for fitting  
  > "In this work, we fit the polarized observations of near event-horizon emission reported by (cite: W22)" (Introduction) [from (cite: W22)]
- ALMA light-curve uncertainty characterization  
  > "For the characterization of uncertainties in the ALMA data see (cite: Wielgus2022_LC), where the formal ALMA light-curve uncertainties were found to be underestimated." (Two-step parameter estimation procedure) [from (cite: Wielgus2022_LC)]
- Dynamic sampler  
  > "we used a dynamic sampler that was introduced by (cite: Higson:2019) with 200 initial live points and 200 points per extra dynamical batch (10 in total)." (Two-step parameter estimation procedure) [from (cite: Higson:2019)]
- Bounding balls and random-walk sampling  
  > "The balls were first mentioned in (cite: Buchner:2016)." (Two-step parameter estimation procedure); "We also used a random walk as our sampling technique. This was developed by (cite: Skilling:2006gxv)." (Two-step parameter estimation procedure) [from (cite: Buchner:2016); (cite: Skilling:2006gxv)]
- Synchrotron cooling-timescale calculation  
  > "Given our best-fit values for $\Theta_{0,s}$ and $B_{0,s}$ we calculated $T_{\textrm{cool}}$ using ( and (cite: moscibrodzka:2011))" (Discussion and conclusions) [from (cite: moscibrodzka:2011)]

### Not stated but needed to reproduce (our reading)

- Exact input light-curve file, access location, polarization conventions, and preprocessing inherited from W22.
- Precise retained timestamps and handling of calibrator gaps when selecting every twentieth sample.
- Widths and truncation rules for the Gaussian priors in log density, log temperature, and log magnetic-field strength.
- Exact ipole and dynesty versions, pipeline source, and random seeds.
- Unambiguous likelihood implementation: the displayed expression leaves the sign of the U residual term ambiguous.
- Ray-tracing integration tolerances and the exact emission-coefficient implementation.
- Background-fit prior ranges, likelihood uncertainties, and sampler configuration.

## Analysis recipe

1. **Select polarized light curves**: Use 9:00–10:30 UTC; retain 35 of 710 points by sampling 1 out of 20; fit Q and U.  
  > "We fit ALMA light curves starting at 9:00 UTC until 10:30 UTC" (Two-step parameter estimation procedure); "Our original data set had 710 data points, but we used 35 of these, sampling 1 out of 20 points." (Two-step parameter estimation procedure); "In our modeling, we only fit Stokes $\mathcal{Q}$ and $\mathcal{U}$ light curves, but we verified Stokes $\mathcal{I}$ and ${\mathcal V}$ for consistency afterward" (Two-step parameter estimation procedure)
   - parameter: Cadence 4 s to 80 s; 70 fitted Q and U values  
  > "which changed cadence very little from 4 s to 80 s." (Two-step parameter estimation procedure); "Hence, we fit only 35 data points (or rather 70 because we took $\mathcal{Q}$ and $\mathcal{U}$ values into account separately)." (Two-step parameter estimation procedure)
   - assumption: Subsampling has little impact because of temporal correlation timescales.  
  > "Because of the temporal correlation timescales involved, the subsampling has little impact on the inference power." (Two-step parameter estimation procedure)
   - fitting: _not stated_
   - validation: _not stated_
2. **Generate polarized hot-spot light curves**: Ray-trace a circular equatorial Gaussian spot; integrate snapshot intensities over the FOV into all four Stokes flux densities.  
  > "The spot lies in a circular orbit in the equatorial plane" (Model); "Synthetic light curves were then generated by creating snapshot images at a predefined sequence of times and integrating their intensities over the FOV into total flux densities in all four Stokes parameters." (Model)
   - software: ipole
   - parameter: FOV=40 M ≈200 μas; 64×64 pixels per frame  
  > "We adopted FOV=40$M$$\approx 200\, \mu$as" (Model); "Due to large numerical cost of these calculations, we adopted a resolution of 64$\times$64 pixels per single frame." (Model)
   - parameter: Gaussian standard deviation fixed at 3 M; boundary n_e,s ≤0.01 n_0,s  
  > "$R_s$ is the size of the Gaussian standard deviation, defining the size of the spot, and it remained fixed at $3M$ to limit the number of parameters." (Model); "Additionally, we used a spot boundary, ignoring matter when $n_{e,s} \leq 0.01n_{0,s}$" (Model)
   - parameter: Exponential temperature evolution; T_ini=2000 M; camera r=1000 M  
  > "We extended the spot models of (cite: Vos:2022) and allowed the Gaussian spot to change its temperature as an exponential function of time." (Model); "We introduce the cooling coefficient $C_{\textrm{coef}}$ and the numerical parameter $T_{\rm{ini}}=2000M$" (Model); "`ipole` tracks light backward in time from the camera position at $r=1000M$ so that the coordinate time $t$ is a negative quantity" (Model)
   - assumption: Relativistic thermal electrons; synchrotron emission, self-absorption, Faraday rotation and conversion  
  > "we assumed that electrons have a relativistic thermal energy distribution function" (Model); "The underlying calculations employ the full relativistic radiative transfer model of `ipole`, including synchrotron emission, self-absorption, and the effects of Faraday rotation and conversion." (Model)
   - assumption: Finite light speed; emission cut below ISCO; Kerr metric  
  > "We self-consistently accounted for the finite velocity of light, that is, we did not employ the commonly used fast light approximation." (Model); "In our model, all emission is cut below the innermost stable circular orbit (ISCO)." (Model); "The space-time is described with the Kerr metric" (Model)
   - assumption: M=4.155×10^6 M_sun  
  > "We assumed a mass of Sgr A\* $M=4.155 \times 10^6\,M_{\odot}$" (Model)
   - fitting: _not stated_
   - validation: Compare 16², 64² and 196² light curves; check primary and secondary image contributions.  
  > "we show the relative difference (in percentile) of the light curves using three different resolutions ($16^2$, $64^2$, and $196^2$)" (Resolution); "The second test we performed determined the relation of the first to the secondary image, and how in particular the latter is affected by the resolution." (Resolution)
3. **Validate parameter recovery**: Controlled bipole run on synthetic data with the same fitted-parameter count and priors as the real-data analysis.  
  > "Finally, before fitting the real data, we performed a controlled `bipole` run using synthetic data to demonstrate the ability of our pipeline to recover the truth value." (Two-step parameter estimation procedure); "The total number of fitted parameters was the same as for the real data" (Two-step parameter estimation procedure); "with the same priors." (Two-step parameter estimation procedure)
   - software: bipole
   - fitting: Inspect trace and corner plots.  
  > "On the left side, we present the trace plot, showing the evolution of the live points throughout the run." (Two-step parameter estimation procedure); "On the right side, we show the corner (or triangle) plot, showing the single and joint distributions for all parameters." (Two-step parameter estimation procedure)
   - validation: All truth values covered by the posteriors.  
  > "All truth values, indicated with red lines, are comfortably covered by the posteriors." (Two-step parameter estimation procedure)
4. **Fit eight spot models**: Fit spot-only Q and U with additive static Q_sha and U_sha; compare cooling, magnetic polarity and Keplerian/non-Keplerian combinations.  
  > "In our first fitting step, we fit emission from the spot alone" (Two-step parameter estimation procedure); "which were simply added to the variable light curves." (Two-step parameter estimation procedure); "We ran eight models that we list in Table [1](#tab:models) to fit the spot component to the ALMA observational data." (Spot fitting)
   - software: ipole, dynesty, bipole
   - parameter: 200 initial live points; 200 per extra dynamical batch; 10 batches  
  > "we used a dynamic sampler that was introduced by (cite: Higson:2019) with 200 initial live points and 200 points per extra dynamical batch (10 in total)." (Two-step parameter estimation procedure)
   - parameter: Terminating log-evidence change 0.01; posterior-exploration weight 100%; random walk  
  > "We used the default stopping criteria, meaning a terminating change in the log-evidence of 0.01." (Two-step parameter estimation procedure); "Additionally, we adopted a weight function that shifted the importance of the posterior exploration (rather than the evidence) to $100\%$." (Two-step parameter estimation procedure); "We also used a random walk as our sampling technique." (Two-step parameter estimation procedure)
   - parameter: i=[90,180°]; a_*=[0.0,0.9]; r_s=[7,15] M  
  > "| i | $[90,180^\circ]$ | Viewing angle (inclination) of the observer: $i=0^\circ$ is face-on, $i=90^\circ$ is edge-on |" (Model); "| $a_*$ | $[0.0,0.9]$ | Dimensionless black hole spin |" (Model); "| $r_{s}$ | $[7,15]$ | Distance of the center of the spot from black hole center ($M$) |" (Model)
   - parameter: n_0,s=[10^4,10^8] cm^-3; Θ_0,s=[1,10^3]; B_0,s=[0.1,10^2] G  
  > "| $n_{0,s}$ | $[10^4,10^8]$ | Electron number density at the center of the spot (cm$^{-3}$) |" (Model); "| $\Theta_{0,s}$ | $[1,10^3]$ | Electron dimensionless temperature at the center of the spot |" (Model); "| $B_{0,s}$ | $[0.1,10^2]$ | Magnetic field strength $(G)$ |" (Model)
   - parameter: φ_cam=[0,360°]; Q_sha=[-1,1] Jy; U_sha=[-1,1] Jy  
  > "| $\phi_{\rm cam}$ | $[0,360^\circ]$ | Location of the camera at the first point of observation (shifts light curves left-right) |" (Model); "| $Q_{\rm sha}$ | $[-1,1]$ | Average background Stokes $Q$ parameter (Jy) |" (Model); "| $U_{\rm sha}$ | $[-1,1]$ | Average background Stokes $U$ parameter (Jy) |" (Model)
   - parameter: PA=[-90°,90°]; C_coef=[10^-5,10^-3] M^-1; K_coef=[0.5,1.2]  
  > "| PA | $[-90^\circ,90^\circ]$ | Position angle of the black hole spin projected on the observer’s screen, measured east of north |" (Model); "| $C_{\textrm{coef}}$ | $[10^{-5},10^{-3}]$ | Coefficient for the exponential cooling ($M^{-1}$) |" (Model); "| $K_{\textrm{coef}}$ | $[0.5,1.2]$ | Coefficient defining the orbital velocity with respect to the Keplerian case |" (Model)
   - assumption: Negligible Faraday effects between the separately fitted components  
  > "This split in the fitting procedure works well as long as both Faraday effects between components are negligible, for example, when the two model components are spatially separated in the images." (Two-step parameter estimation procedure)
   - assumption: σ_Q,j=(ε_s|Q_j|+ε_t)^0.5 and σ_U,j=(ε_s|U_j|+ε_t)^0.5; ε_s=0.02; ε_t=0.01  
  > "\sigma_{Q,j} &=& (\epsilon_{s}|Q_j| + \epsilon_{t})^{0.5}" (Two-step parameter estimation procedure); "\sigma_{U,j} &=& (\epsilon_{s}|U_j| + \epsilon_{t})^{0.5}" (Two-step parameter estimation procedure); "where $\epsilon_{s}=0.02$ is the assumed systematic error, and $\epsilon_{t}=0.01$ represents thermal noise." (Two-step parameter estimation procedure)
   - fitting: Dynamic nested sampling; ray-tracing per log-likelihood evaluation; log-normal plasma priors, flat remaining priors.  
  > "`dynesty` is a Bayesian tool capable of performing dynamic nested sampling." (Two-step parameter estimation procedure); "We embedded `ipole` so that the sampler called a ray-tracing operation for every log-likelihood evaluation." (Two-step parameter estimation procedure); "For $n_{0,s},\,\Theta_{0,s}$, and $B_{0,s}$ we sampled the log space with Gaussian priors centered in the middle of their log ranges (i.e., log-normal priors). For the remaining parameters we considered, we assume flat priors." (Two-step parameter estimation procedure)
   - validation: Controlled synthetic recovery before fitting real data  
  > "Finally, before fitting the real data, we performed a controlled `bipole` run using synthetic data to demonstrate the ability of our pipeline to recover the truth value." (Two-step parameter estimation procedure)
5. **Compare models and held-out Stokes parameters**: Compare evidence and reduced χ²; inspect I and V from best-fit realizations without fitting their background shifts.  
  > "The low value of $\chi_{\rm eff}^2=0.34$ together with the log(Evidence) and the smooth posteriors make nc_fb_nk our best-bet model." (Spot fitting); "In this section, we report the behavior of the Stokes $\mathcal{I}$ and $\mathcal{V}$ light curves for the best-fit realizations of the eight discussed models." (Cross-checking with other Stokes parameters); "We did not fit for the best (sha) values to Stokes $\mathcal{I}$ (and $\mathcal{V}$, see below)." (Cross-checking with other Stokes parameters)
   - assumption: I light-curve shifts accommodate expected background emission.  
  > "The shift (sha) of the light curves is just for visual aid, and it accommodates the contribution we expect from the background (the accretion disk)." (Cross-checking with other Stokes parameters)
   - fitting: Use highest-likelihood realizations from each run.  
  > "using the model with the highest likelihood from each run as parameters for the ray-tracing." (Spot fitting)
   - validation: Best-bet nc_fb_nk also recovers observed V best.  
  > "In particular, the best-bet model nc_fb_nk recovers the observed Stokes $\mathcal{V}$ best, which is a strong independent argument in support of the model." (Cross-checking with other Stokes parameters)
6. **Fit static background plasma**: Fit each inferred Q_sha,U_sha pair with the ADAF background density, temperature and magnetic-field model.  
  > "Our goal was to obtain the density, temperature, and magnetic field strengths of the background component." (Background emission); "since the background is static, we only need one point (or rather two, for $\mathcal{Q}$ and $\mathcal{U}$) to make the fit." (Background emission)
   - software: ipole
   - parameter: Fix a_*, i, PA and, for non-Keplerian models, K_coef to spot-fit values.  
  > "we fixed all the geometric parameters ($a_*$, $i$, PA), plus $K_{\rm coef}$ for non-Keplerian models, at the values obtained in the spot-fitting" (Background emission)
   - parameter: Density ∝r^-1.5 exp[-cos²θ/(2σ²)], temperature ∝r^-0.84, magnetic strength ∝r^-1; σ=0.3  
  > "n_{e,bg}&=&n_{0,bg}\left(\frac{r}{r_g}\right)^{-1.5}\exp{\left(\frac{-\cos^2{\theta}}{2\sigma^2}\right)}" (Model); "\Theta_{e,bg}&=& \Theta_{0,bg} \left(\frac{r}{r_g}\right)^{-0.84}" (Model); "B_{bg} &=& B_{0,bg}\left(\frac{r}{r_g}\right)^{-1}" (Model)
   - assumption: Disk and spot share K_coef; omit emission inside ISCO.  
  > "The choice to simulate the disk with the same $K_{\textrm{coef}}$ as the spot is an assumption" (Background emission); "The exclusion of the radiation originating inside the ISCO constitutes an additional limitation." (Background emission)
   - assumption: Disk vertical thickness σ=0.3  
  > "$\sigma=0.3$ characterizes the disk vertical thickness" (Model)
   - fitting: Three-parameter background runs; use posterior peaks to calculate I_BG,V_BG.  
  > "Using the peaks of the posteriors from the three parameter runs, we calculated Stokes $\mathcal{I}_{\textrm{BG}}$, $\mathcal{V}_{\textrm{BG}}$ produced from the background disk." (Background emission)
   - validation: Compare predicted I_BG,V_BG with visual shifts and ALMA averages; default-polarity models match shadow components fairly well.  
  > "Our motivation was to test whether any of the Stokes values match the reported $\mathcal{I}_{\textrm{sha}}$, $\mathcal{V}_{\textrm{sha}}$ values" (Background emission); "All values from the default $B_{\rm field}$ models match the shadow components fairly well." (Background emission)
7. **Derive physical timescales and inspect spin sensitivity**: Calculate orbital periods and synchrotron cooling times; change best-bet spin to zero and separate primary/secondary image light curves.  
  > "All orbital periods of the spots are reported in Table [4](#tab:logz)" (Spot fitting); "Given our best-fit values for $\Theta_{0,s}$ and $B_{0,s}$ we calculated $T_{\textrm{cool}}$" (Discussion and conclusions); "we present what happens to our best-bet model if we keep all parameters the same and only change the spin to $a_*=0$." (Spin estimates)
   - parameter: P=(2π/K_coef)(r_g/c)[(r/r_g)^1.5+a_*]  
  > "P=\frac{2\pi}{K_{\textrm{coef}}}\frac{r_g}{c}\left(\left(\frac{r}{r_g}\right)^{1.5} + a_*\right)" (Model)
   - parameter: T_cool=11 h (B/10G)^-2 (Θ/50)^-1  
  > "T_{\textrm{cool}}= 11\,{\rm h} \left(\frac{B}{10G}\right)^{-2} \left(\frac{\Theta}{50}\right)^{-1}" (Discussion and conclusions)
   - assumption: Thermal electron distribution for cooling-time interpretation  
  > "However, we assumed that the electrons in the spot have a thermal distribution function." (Discussion and conclusions)
   - fitting: _not stated_
   - validation: Compare cooling with loop disappearance; inspect spin effects in primary and secondary images.  
  > "In observational data, the $\mathcal{Q}-\mathcal{U}$ loop disappears on timescales of about $\sim2$ h" (Discussion and conclusions); "we plot the light curves for the primary and secondary image separately." (Spin estimates)

## Software

- **ipole** : Covariant general relativistic polarized radiative transfer and synthetic Stokes maps  
  > "The model is fully built within `ipole`, which is a ray-tracing code for the covariant general relativistic transport of polarized light in curved space-times developed by (cite: Monika2018)." (Model)
- **dynesty** : Bayesian dynamic nested sampling  
  > "`dynesty` is a Bayesian tool capable of performing dynamic nested sampling." (Two-step parameter estimation procedure)
- **bipole** : Fitting pipeline combining ipole simulations and dynesty  
  > "A comprehensive list of all the parameters and their ranges used in our fitting pipeline, referred to as `bipole` in the next sections" (Two-step parameter estimation procedure); "To model the ALMA data, we set up a fitting framework that combined our `ipole` simulations with the `dynesty` software" (Two-step parameter estimation procedure)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fitting viewing angles across spot models | (155,160) | not stated | deg | 4 | all spot models show consistently similar best-fitting viewing angles $i \in(155,160)$ deg and a spot orbital radius $r_s\in(9,12.5)M$. |
| Spot orbital radii across models | (9,12.5) | not stated | M | 4 | all spot models show consistently similar best-fitting viewing angles $i \in(155,160)$ deg and a spot orbital radius $r_s\in(9,12.5)M$. |
| Black-hole spin estimates | ∼0.8-0.9 | not stated | dimensionless | 4 | Although we obtain a black hole spin estimate of high values ($a_* \sim 0.8-0.9$) in all cases, we did not consider negative spins in our priors. |
| PA for models except c_fb_nk | [-10,10] or [170,190] | not stated | deg | 4 | All models except for c_fb_nk also consistently show PA $\in[-10,10]$ deg (or $[170,190]$ deg |
| Approximate spot electron density range | (10^6,3×10^7) | not stated | particles/cm^3 | 4 | All models consistently show that our spot parameters should be in an approximate range of $n_{\rm 0,s}\in(10^6,3\times10^7)$ ${\rm particles/cm^3}$, $\Theta_{\rm 0,s} \in(15,70)$, $B_{\rm 0,s}\in(2,40)$ G. |
| Approximate spot dimensionless electron temperature range | (15,70) | not stated | dimensionless | 4 | All models consistently show that our spot parameters should be in an approximate range of $n_{\rm 0,s}\in(10^6,3\times10^7)$ ${\rm particles/cm^3}$, $\Theta_{\rm 0,s} \in(15,70)$, $B_{\rm 0,s}\in(2,40)$ G. |
| Approximate spot magnetic-field strength range | (2,40) | not stated | G | 4 | All models consistently show that our spot parameters should be in an approximate range of $n_{\rm 0,s}\in(10^6,3\times10^7)$ ${\rm particles/cm^3}$, $\Theta_{\rm 0,s} \in(15,70)$, $B_{\rm 0,s}\in(2,40)$ G. |
| Particularly preferred non-Keplerian K_coef range | (0.65-0.85) | not stated | dimensionless | 4 | Additionally, the non-Keplerian models prefer $K_{\rm coef}\in(0.5,1)$, and in particular, $(0.65-0.85)$. |
| nc_fb_nk log Z | -50.4 | ±0.3 | dimensionless | 5 | / nc_fb_nk / $-50.4$ / $0.34$ / $91.2$ / $77$ /; Evidence ($\log Z \pm0.3$) |
| nc_fb_nk reduced χ² | 0.34 | not stated | dimensionless | 5 | / nc_fb_nk / $-50.4$ / $0.34$ / $91.2$ / $77$ / |
| nc_fb_nk orbital period | 91.2 | not stated | min | 7 | / nc_fb_nk / $-50.4$ / $0.34$ / $91.2$ / $77$ / |
| nc_fb_nk synchrotron cooling timescale | 77 | not stated | h | 7 | / nc_fb_nk / $-50.4$ / $0.34$ / $91.2$ / $77$ / |
| c_fb_k synchrotron cooling timescale | 1 | not stated | h | 7 | / c_fb_k / $-65.4$ / $1.22$ / $87.2$ / $1$ / |
| c_fb_nk orbital period | 155.5 | not stated | min | 7 | / c_fb_nk / $-92.8$ / $2.05$ / $155.5$ / $52$ / |
| c_fb_nk reduced χ² | 2.05 | not stated | dimensionless | 5 | / c_fb_nk / $-92.8$ / $2.05$ / $155.5$ / $52$ / |
| nc_fb_nk background linear-polarization offsets Q_sha,U_sha | 0.11, -0.12 | not stated | Jy | 4 | / nc_fb_nk     /         $0.11$          /         $-0.12$         / |
| nc_fb_nk background I_BG,V_BG | 2.86, +0.24 | not stated | Jy | 6 | / nc_fb_nk / $2.86$ / $+0.24$ / $1.75$ / $-0.028$ / |
| Mean Q and U deviations in resolution test | 2%, 1.5% | not stated | dimensionless | 2 | This amounts to $2\%$ for $\mathcal{Q}$ and $1.5\%$ for $\mathcal{U}$. |
| Reduced χ² after changing best-bet spin to a_*=0 | ∼1.5 | not stated | dimensionless | 7 | only change the spin to $a_*=0$. While the difference is not dramatic (the model still produces $\chi^2_{\rm eff}\sim1.5$), it is certainly noticeable. |

## Qualitative findings

- Preferred spot model has no cooling, a non-Keplerian orbit, and magnetic field toward the observer.  
  > "made with a flipped $B_{\textrm{field}}$, no cooling, and a non-Keplerian orbit." (Discussion and conclusions); "magnetic field vector arrow pointing toward the observer for viewing angles $i>90$ deg" (Discussion and conclusions); "The low value of $\chi_{\rm eff}^2=0.34$ together with the log(Evidence) and the smooth posteriors make nc_fb_nk our best-bet model." (Spot fitting)
- Inferred viewing geometry implies clockwise hot-spot rotation on the sky.  
  > "The viewing angle close to 180 deg determines a clockwise hot-spot rotation on the sky." (Discussion and conclusions)
- Spot-preferred magnetic polarity produces the wrong background circular-polarization sign.  
  > "the models with a magnetic field pointing toward the observer, which seem to produce better results for the spot fitting, have Stokes $\mathcal{V}_{\textrm{BG}}$ with the opposite sign to $\mathcal{V}_{\textrm{sha}}$ and the ALMA average value." (Discussion and conclusions)
- Secondary-image emission drives the spin preference.  
  > "The dominant effect comes from the secondary image, which is formed by photons approaching the photon shell, which is located much closer to the black hole." (Spin estimates)

## Claim tuples

- H: A hot-spot model can describe the polarized ALMA loop and distinguish orbital and magnetic configurations. | E: Fit eight combinations of cooling, magnetic polarity and orbital motion; compare evidence and reduced χ². | R: nc_fb_nk has log Z=-50.4 and reduced χ²=0.34. | F: The preferred spot has no cooling, non-Keplerian motion and flipped magnetic polarity. | **supported**
- H: The Q,U-preferred configuration should also agree with circular polarization. | E: Inspect V light curves excluded from fitting. | R: nc_fb_nk recovers observed V best; default-polarity models fail to recover its variability. | F: Circular polarization independently favors the best-bet spot model. | **supported**
- H: Polarized hot-spot light curves constrain viewing geometry and orbital scale. | E: Compare posterior estimates across all spot models. | R: i∈(155,160) deg; r_s∈(9,12.5) M; preferred period approximately 90 minutes except one model. | F: The models consistently favor nearly face-on clockwise motion and similar orbital scales. | **supported**
- H: Radiative cooling explains disappearance of the loop on an approximately two-hour timescale. | E: Calculate thermal synchrotron cooling times from fitted magnetic fields and electron temperatures. | R: The best-bet nc_fb_nk gives 77 h; c_fb_k gives 1 h. | F: Only c_fb_k reasonably matches the disappearance timescale under the thermal-electron assumption. | **partially**
- H: Separately fitted spot and static background components provide a consistent polarized-emission description. | E: Fit background Q,U offsets, then compare predicted background I,V with observed or shifted values. | R: Background Q,U can be reproduced, but spot-preferred polarity gives the opposite background V sign. | F: The two-step approach passes a limited sanity check; different spot/disk field morphology or a combined model may be needed. | **partially**

## Reasoning

- Why this data: Post-X-ray-flare Q,U loops interpreted as an orbiting bright spot  
  > "We focused on 230 GHz data that were collected immediately following an X-ray flare detected by the *Chandra* observatory on April 11 2017 (cite: eht:2022_paperII; Wielgus2022_LC)." (Introduction); "Stokes $\mathcal{Q}-\mathcal{U}$ loops, interpreted as a signature of a bright spot around the black hole, were observed within the first two hours of this observing window." (Two-step parameter estimation procedure)
- Why this method: Nested sampling handles degenerate, potentially multimodal posteriors; subsampling reduces computational cost.  
  > "it is compatible with low-dimensional but highly degenerate and potentially multimodal posteriors" (Two-step parameter estimation procedure); "To be able to produce a fit on timescales shorter than a year, we sub-sampled the ALMA data set" (Two-step parameter estimation procedure)
- Alternative: Cooling/no cooling, default/flipped magnetic polarity, Keplerian/non-Keplerian models  
  > "We considered eight models with a varying level of complexity, distinguished by choices regarding dynamically important cooling, non-Keplerian motion, and magnetic field polarity." (abstract)
- Alternative: Keplerian background disk with a sub-Keplerian spot remains an alternative.  
  > "other possibilities could be meaningful as well, for instance, a Keplerian disk with a sub-Keplerian spot." (Background emission)
- Alternative: Nonthermal electrons could change inferred cooling times.  
  > "A different assumption, for instance, a nonthermal electron distribution function, could lead to different $T_{\textrm{cool}}$." (Discussion and conclusions)
- Alternative: Plasmoid formation as an alternative physical origin of hot spots  
  > "we note that there are other possibilities, such as the formation of plasmoids (cite: ripperda20; elmellah23; vos23)." (Discussion and conclusions)
- Alternative: Separate spot/disk magnetic morphology or lensing-induced background circular-polarization sign reversal  
  > "A flipped magnetic field for the disk, or even better, a separate morphology entirely for the spot and disk, might be the optimal solution." (Discussion and conclusions); "Another possibility is that the shadow component has a negative circular polarization due to the gravitational lensing effect" (Discussion and conclusions)
- How they decided it was enough: Log-evidence stopping change 0.01; synthetic recovery; resolution differences below the adopted error level  
  > "We used the default stopping criteria, meaning a terminating change in the log-evidence of 0.01." (Two-step parameter estimation procedure); "All truth values, indicated with red lines, are comfortably covered by the posteriors." (Two-step parameter estimation procedure); "the general behavior remains very similar and the relative differences are below the error level of the data." (Model)
- Limitation (authors): Static background omits emission inside ISCO and variability.  
  > "our model for the background emission (the shadow component) neither includes emission from regions within the ISCO nor has any variability." (Two-step parameter estimation procedure)
- Limitation (authors): Exponential temperature evolution is not a physical synchrotron-cooling model.  
  > "This is a simplistic general prescription that does not aim to simulate the synchrotron cooling, but rather enabled us to explore the impact of cooling without making additional assumptions regarding its physical mechanisms." (Model)
- Limitation (authors): Spot shearing and interactions with the background are omitted.  
  > "spot properties that we did not include in our simple model, such as the shearing of the spot or other spot interaction with the background flow (cite: Tiede2020)." (Discussion and conclusions)
- Limitation (authors): Negative spins excluded; orbital period only weakly depends on spin.  
  > "For the expected orbital radii, the period" (Discussion and conclusions); "only weakly depends on the black hole spin." (Discussion and conclusions); "we did not consider negative spins in our priors. We therefore missed some of the parameter space." (Discussion and conclusions)
- Limitation (authors): Background fit has limited inference power and remains dissociated from the spot component.  
  > "Overall, this second step does not offer much inferring power at this point" (Background emission); "it remains somewhat dissociated from the spot component." (Discussion and conclusions)
- Caveat (inferred, ours): The preferred spin lies near the upper prior boundary; a wider spin prior and nuisance-model sensitivity tests are needed.
- Caveat (inferred, ours): Temporal correlations motivate subsampling, but the supplied text does not give a covariance model or a quantitative full-cadence inference comparison.
- Caveat (inferred, ours): The displayed likelihood and error prescription require implementation-level clarification before numerical answer keys can be reproduced.
- Caveat (inferred, ours): A three-parameter background fitted to two Stokes values is strongly degenerate; its inferred plasma properties need additional constraints.
- Caveat (inferred, ours): The magnetic polarity preferred for the spot conflicts with the background V sign under the shared model assumptions.
- Caveat (inferred, ours): The quoted overall plasma and radius ranges are summaries across models, not stated credible intervals.
- Caveat (inferred, ours): One synthetic recovery example and a resolution test at a random parameter combination do not establish coverage or numerical accuracy across the entire posterior.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Input polarized light-curve file and an explicit public access location.
- Missing: Original calibration and polarization-processing recipe, or an identified ready-to-fit data product.
- Missing: Exact sample selection and timestamp conventions.
- Missing: Executable bipole source and configuration, including software versions.
- Missing: Log-normal prior widths and background-fit priors.
- Missing: Confirmed likelihood implementation and error units.
- Missing: Posterior samples and numerical best-fit parameter vectors for all models.
- Missing: Ray-tracing numerical tolerances and emission settings.
- Data volume (inferred): Small light-curve input: 35 retained epochs from 710 original points. Raw ALMA visibility volume cannot be estimated from the supplied text.
- Score (inferred): 5/5, 5/10: project identification, model equations, parameter ranges, sampler settings and numerical comparisons are provided; input access, runnable code, prior widths and several implementation details are missing.
- Rediscovery candidate: no, Main results are numeric, but public availability is not stated and the supplied recipe lacks input access, code and complete prior/likelihood specifications.

## Links

- Method: (cite: Vos:2022) (Detailed semi-analytic model adopted and extended.)
- Method: (cite: Brod-Loeb2006); (cite: Fraga-Encinas:2016nft) (Earlier hot-spot model inspiration.)
- Method: (cite: Monika2018) (ipole polarized general relativistic radiative-transfer code.)
- Method: (cite: Speagle:2019ivv); (cite: sergey_koposov_2023_7995596) (dynesty Bayesian sampling software.)
- Method: (cite: Higson:2019) (Dynamic sampler.)
- Method: (cite: Buchner:2016) (Bounding balls.)
- Method: (cite: Skilling:2006gxv) (Nested sampling and random-walk sampling technique.)
- Method: (cite: moscibrodzka:2011) (Synchrotron cooling-timescale calculation.)
- Method: (cite: Wielgus2022_LC) (ALMA light-curve uncertainty characterization.)
- Companion: (cite: W22) (Published polarized observations and earlier interpretation of the same hot-spot event.)
- Companion: (cite: Vos:2022) (Previous model expanded in this work.)
- Related: Event Horizon Telescope (EHT)

## Checks

```json
{
 "quotes": 172,
 "quotes_ok": 172,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 120,
  "stated": 80,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
